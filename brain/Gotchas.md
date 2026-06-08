---
date: 2026-06-02
description: "Things that have bitten before and will bite again — pitfalls, edge cases, and testing traps"
tags:
  - brain
---

# Gotchas

Things that have bitten before and will bite again.

## Claude Code ECONNRESET over work OpenVPN (recurring, fixed 2026-06-02)

**Symptom**: Claude Code throws `ECONNRESET` intermittently. A prior fix appeared to work, then the errors returned.

**Root cause**: The work OpenVPN installs IPv6 default routes pointing into its tunnels (`netstat -rn` shows four `default → fe80::%utunX` entries under Internet6). When the tunnel is healthy, IPv6 works; when it reconnects or routes go stale, IPv6 connections reset. `api.anthropic.com` has an AAAA record (`2607:6bc0::10`) and the macOS resolver returns it first, so Node reaches for IPv6.

**Why the first fix failed twice over**:
1. `--dns-result-order=ipv4first` only *reorders* DNS results. Node 20+ enables Happy Eyeballs (`autoSelectFamily`) by default, which races IPv4 and IPv6 sockets simultaneously — IPv6 still gets used.
2. The flag lived only in `~/.claude/settings.json` `env`, which Claude Code reads *after* its own Node process starts. It propagated to subprocesses but never governed the main process.

**The durable fix** (both layers, applied 2026-06-02, Node v24.15.0, Claude Code 2.1.161):
- `NODE_OPTIONS="--dns-result-order=ipv4first --no-network-family-autoselection"` — the second flag disables Happy Eyeballs racing so Node strictly uses IPv4.
- Set in **both** `~/.claude/settings.json` `env` (covers subprocesses/MCP servers) and `~/.zshrc` export (covers the main process at launch). Backup at `~/.zshrc.bak-econnreset`.

**If it recurs anyway**: check `echo $NODE_OPTIONS` inside the failing session first. If the flags are present and resets continue, the next suspect is MTU on the tunnel (`utun1` runs at 1380) — test with `curl -4` against `api.anthropic.com` during a failure window to confirm IPv4 itself is resetting before touching `mssfix`/`tun-mtu`.

### Second recurrence — the launch-method hole (closed 2026-06-08, Node v24.15.0, Claude Code 2.1.168)

**Why it came back**: The 2026-06-02 fix lived in `~/.zshrc` (+ `settings.json` env). `.zshrc` is sourced **only by interactive login shells**. Launch Claude Code from the Dock, Spotlight, Raycast, or an IDE extension and no shell runs — so the main process started with **no `NODE_OPTIONS`**, Happy Eyeballs raced IPv6 over the flapping VPN tunnel, and `ECONNRESET` returned. Confirmed: `launchctl getenv NODE_OPTIONS` was empty, and a `launchctl asuser` (GUI-equivalent) node launch saw no flags.

**Diagnosis that ruled everything else out**: with the flags present in a terminal session, `net.getDefaultAutoSelectFamily()` returns `false` and **both** `https` and `undici`/`fetch` connect via IPv4 (`family=IPv4`, `160.79.104.10`). IPv4 to `api.anthropic.com` routes over `en0 → 192.168.1.1` (split tunnel, **bypasses the VPN entirely**) — 10/10 rapid handshakes succeed at ~15ms, so MTU was never the culprit. The single A record (TTL 300) made an `/etc/hosts` pin tempting but it carries IP-rotation outage risk, so the fix stays at the env layer.

**The durable close** (no DNS/routing changes, so no IP-rotation hazard):
- `~/.zshenv` — exports the same `NODE_OPTIONS`. Sourced by **every** zsh invocation (non-login, non-interactive, scripts), not just login shells.
- `~/Library/LaunchAgents/com.spencer.node-options.plist` — runs `launchctl setenv NODE_OPTIONS "..."` at login (`RunAtLoad`), so **GUI-launched** apps inherit it. Persists across reboots. Loaded live with `launchctl bootstrap gui/$(id -u)` + a one-time `launchctl setenv` so it took effect without a reboot.
- Coverage matrix now: terminal (`.zshrc`) ✓, any zsh (`.zshenv`) ✓, GUI/launchd (LaunchAgent) ✓, MCP subprocesses (`settings.json`) ✓. All four verified to force IPv4.

**If it recurs a third time**: `launchctl getenv NODE_OPTIONS` should be non-empty — if it is empty, the LaunchAgent unloaded (`launchctl list | grep node-options`); re-bootstrap it. If the flags are present everywhere and resets still happen, the env layer is exhausted — only then move to the tunnel-MTU investigation above. Backups: `~/.zshrc.bak-econnreset`, `~/.zshrc.bak-econnreset-20260608`.

## Google Drive MCP does not convert HTML uploads to Google Docs (2026-06-03)

**Symptom**: `/om-case-export` (and any flow that uploads `text/html` via `mcp__claude_ai_Google_Drive__create_file` expecting a Google Doc) produces a raw `.html` file, not a Doc. `get_file_metadata` shows `mimeType: text/html` and a `/file/d/.../view` URL.

**Root cause**: The Drive `create_file` tool only auto-converts `text/plain` → Doc and `text/csv` → Sheet. `text/html` is not in the default-conversion set. Passing the deprecated `mimeType: application/vnd.google-apps.document` target does not force conversion either. `copy_file` exposes no target-mimeType for conversion.

**Workaround**: The uploaded `.html` is still usable — open it in Drive and choose **File → Open with → Google Docs** to render formatting into an editable Doc. A `.docx` (python-docx is installed, v1.2.0) opens directly formatted, but base64-encoding a multi-case docx is too large to round-trip through the tool call, so HTML + open-with is the practical path. No Drive delete tool is exposed — junk/test uploads must be trashed manually.

Skill now documents this: [[Skills]] → `om-case-export` Step 4.

Related: [[Key Decisions]]
