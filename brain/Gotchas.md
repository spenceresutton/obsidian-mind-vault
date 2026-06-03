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

Related: [[Key Decisions]]
