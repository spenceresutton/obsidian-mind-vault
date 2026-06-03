---
date: 2026-04-07
description: "Vault-specific workflows and slash commands — reusable patterns for review prep, project tracking, and vault maintenance"
tags:
  - brain
  - index
---

# Skills

Custom slash commands, subagents, and reusable workflows. Defined in `.claude/commands/` and `.claude/agents/`.

## Slash Commands

### Daily Workflow

| Command | Purpose |
|---------|---------|
| `/om-standup` | Morning kickoff — load context, review yesterday, surface tasks, identify priorities |
| `/om-dump` | Freeform capture — dump anything, gets routed to the right notes automatically |
| `/om-wrap-up` | Full session review — verify notes, indexes, links, suggest improvements. Auto-triggered on "wrap up". |

### Editing & Synthesis

| Command | Purpose |
|---------|---------|
| `/om-humanize` | Voice-calibrated editing — makes Claude-drafted text sound like you wrote it |
| `/om-weekly` | Weekly synthesis — cross-session patterns, North Star alignment, uncaptured wins |

### Meeting Prep & Capture

| Command | Purpose |
|---------|---------|
| `/om-prep-1on1` | Prep for an upcoming 1:1 — load person context, open items, wins to share, suggested agenda |
| `/om-capture-1on1` | Capture 1:1 meeting transcript into structured vault note with quotes, action items, DM context |
| `/om-incident-capture` | Capture incident from Slack channels/DMs into structured vault notes — timeline, people, analysis, brag entry |
| `/om-slack-scan` | Deep scan Slack channels/DMs for evidence — extracts timestamped touchpoints, organizes by context |
| `/om-meeting` | Prep for any meeting by topic — subject-forward briefing with open items, blockers, and brainstormed considerations |
| `/om-intake` | Process meeting notes inbox — classify raw exports in `work/meetings/` and route to the right vault notes |

### Performance & Review

| Command | Purpose |
|---------|---------|
| `/om-peer-scan` | Deep scan a peer's GitHub PRs for review prep — produces structured analysis saved to `perf/evidence/` |
| `/om-review-brief` | Generate review brief (manager or peer version) from vault data |
| `/om-self-review` | Write self-assessment for review tool — projects, competencies, principles |
| `/om-review-peer` | Write peer review — projects, principles, performance summary |

### Vault Maintenance

| Command | Purpose |
|---------|---------|
| `/om-vault-audit` | Deep structural audit — indexes, frontmatter, links, Bases, folder placement, stale context |
| `/om-vault-upgrade` | Import content from an existing vault — detects version, classifies notes, transforms frontmatter, rebuilds indexes |
| `/om-project-archive` | Move completed project from `work/active/` to `work/archive/YYYY/`, update all indexes |

### Navigator Case Management

| Command | Purpose |
|---------|---------|
| `/om-case-ingest` | Pull all cases from the St. Joseph Sanity Test Google Doc and import to `reference/Navigator/Cases/approved/` |
| `/om-case-analyze` | Analyze all approved cases to build or update [[brain/Case Style Guide]] — challenge taxonomy, anti-patterns, voice |
| `/om-case-generate` | Generate a new case with style calibration from approved cases and available guidelines; saves to `pending/` |
| `/om-case-review` | Review pending cases one at a time — approve, revise, or reject; mirrors LinkedIn post approval workflow |
| `/om-case-export` | Export approved cases formatted for the Google Doc — markdown block, new Doc, or append to existing |

## Usage Notes

**Daily:**
- `/om-standup` replaces the manual session start — reads North Star, active work, tasks, git log
- `/om-dump` processes freeform text and routes each piece to the correct note type and folder
- `/om-wrap-up` is auto-triggered when you say "wrap up" — runs full session review

**Editing & Synthesis:**
- `/om-humanize` calibrates against your actual writing samples, not a word blacklist. Detects context from frontmatter (review → corporate-confident, incident → precise, 1:1 → conversational). Run after drafting any note to make it sound human.
- `/om-weekly` bridges standup and review brief — run at end of week for cross-session patterns, North Star drift, and uncaptured wins. Output is transient by default; offer to promote findings to brag doc or North Star.

**Capture:**
- `/om-capture-1on1` handles transcripts, raw notes, or summaries
- `/om-incident-capture` takes Slack URLs and produces structured incident documentation
- `/om-slack-scan` should be run AFTER `/om-peer-scan` to add context beyond code (leadership, communication, collaboration evidence)

**Performance:**
- `/om-peer-scan` works best when launched as parallel agents (one per person)
- `/om-review-brief` needs the private brief to exist first — it generates filtered versions from it

**Maintenance:**
- `/om-vault-audit` should be run at the end of substantial sessions — catches stale indexes and mixed context
- `/om-vault-upgrade` imports content from an existing vault (older obsidian-mind or any Obsidian vault). Detects version, classifies notes, transforms frontmatter, fixes wikilinks, rebuilds indexes. Use `--dry-run` to preview.
- `/om-project-archive` handles the active/ → archive/ move with index updates

## Subagents

| Agent | Purpose | Invoked by |
|-------|---------|------------|
| `brag-spotter` | Proactively finds uncaptured wins and competency gaps | `/om-wrap-up`, `/om-weekly` |
| `context-loader` | Loads all vault context about a person, project, incident, or concept | Direct — "load context on X" |
| `cross-linker` | Finds missing wikilinks, orphans, broken backlinks across the vault | `/om-vault-audit` |
| `people-profiler` | Bulk create/update person notes from Slack profiles | `/om-incident-capture` |
| `review-prep` | Aggregates all performance evidence for a given review period | `/om-review-brief` |
| `slack-archaeologist` | Full Slack reconstruction — reads every message, thread, profile, produces unified timeline | `/om-incident-capture` |
| `vault-librarian` | Deep vault maintenance — orphan detection, broken links, frontmatter validation, stale notes | `/om-vault-audit` |
| `review-fact-checker` | Verify every claim in a review draft against vault sources | `/om-self-review`, `/om-review-peer` |
| `vault-migrator` | Classify, transform, and migrate content from a source vault | `/om-vault-upgrade` |

Subagents run in isolated context windows via `.claude/agents/`. They don't pollute the main conversation.

## Hooks

| Hook | When | What |
|------|------|------|
| SessionStart | On startup/resume | QMD re-index, inject North Star, active work, recent changes, tasks, file listing |
| UserPromptSubmit | Every message | Classify content (decision, incident, 1:1, win, architecture, person, project update) and inject routing hints |
| PostToolUse | After writing `.md` | Validates frontmatter, checks for wikilinks |
| PreCompact | Before context compaction | Back up session transcript to `thinking/session-logs/` |
| Stop | End of session | Checklist: archive, update indexes, check orphans |

## Semantic Search (QMD)

If QMD is installed (`npm install -g @tobilu/qmd`), the vault has semantic search. Every command takes `--index <name>` where `<name>` is `vault-manifest.json`'s `qmd_index` field (default: `obsidian-mind`):

- `qmd --index <name> query "..."` — hybrid BM25 + vector + LLM reranking (best quality)
- `qmd --index <name> search "..."` — fast BM25 keyword search
- `qmd --index <name> vsearch "..."` — semantic vector search (exploratory)
- `qmd --index <name> update && qmd --index <name> embed` — refresh index after bulk changes

SessionStart hook runs `qmd --index <name> update` automatically, reading the index name from the manifest. First-time setup on a fresh clone: `node --experimental-strip-types scripts/qmd-bootstrap.ts`. See `.claude/skills/qmd/SKILL.md` for full reference, and [[Memories]] for the topics QMD is most often asked to find across the vault.

## Workflow: Weekly Review

1. **`/om-weekly`** — synthesize the week's activity, check alignment, find patterns
2. Promote any uncaptured wins to brag doc
3. Update North Star if focus shifted
4. **`/om-wrap-up`** — close the session cleanly

## Workflow: Full Review Cycle Prep

1. **`/om-review-brief manager`** — generate the manager context transfer doc
2. **`/om-review-brief peers`** — generate the peer context transfer doc
3. **`/om-peer-scan`** (parallel, one per peer) — deep scan each peer's PRs
4. **`/om-slack-scan`** — scan relevant channels for your own evidence + peer context
5. **`/om-capture-1on1`** — capture the review 1:1 with your manager
6. **`/om-vault-audit`** — tidy up after all the new data

## Workflow: Project Ramp-Up

1. **`/om-slack-scan`** — scan project channels for history and decisions
2. **`/om-peer-scan`** (if needed) — understand what teammates have already built
3. Create work note from gathered context
4. **`/om-vault-audit`** — ensure everything links properly

---

## obsidian-second-brain Global Commands

Installed at `~/.claude/skills/obsidian-second-brain/`. Commands copied to `~/.claude/commands/`. These are available in any Claude session, not just obsidian-mind.

### Research Toolkit

| Command | Purpose |
|---------|---------|
| `/x-read` | Read and save content from X/Twitter |
| `/x-pulse` | Scan X for trends on a topic |
| `/research` | AI-powered research via Perplexity — findings save to vault |
| `/research-deep` | Deep research with multiple sources |
| `/notebooklm` | NotebookLM integration for synthesis |
| `/youtube` | Extract and save YouTube content |

### Vault Operations

| Command | Purpose |
|---------|---------|
| `/obsidian-save` | Save conversation content to vault |
| `/obsidian-capture` | Quick capture to inbox |
| `/obsidian-task` | Create or update a task |
| `/obsidian-find` | Search vault for a topic |
| `/obsidian-connect` | Find and create missing links |
| `/obsidian-health` | Quick vault health check |
| `/obsidian-log` | Append to vault log |
| `/obsidian-reconcile` | Reconcile duplicate or conflicting notes |

### Learning & Development

| Command | Purpose |
|---------|---------|
| `/obsidian-learn` | Save a learning to the vault |
| `/obsidian-daily` | Daily note operations |
| `/obsidian-recap` | Recap recent vault activity |
| `/obsidian-emerge` | Surface emerging patterns |
| `/obsidian-challenge` | Track a challenge or obstacle |
| `/obsidian-graduate` | Promote a learning to a permanent note |

### People & World

| Command | Purpose |
|---------|---------|
| `/obsidian-person` | Create or update a person note |
| `/obsidian-world` | Capture external world events |

### Projects & Decisions

| Command | Purpose |
|---------|---------|
| `/obsidian-project` | Create or update a project note |
| `/obsidian-adr` | Record an architectural decision |
| `/obsidian-decide` | Capture a decision with context |
| `/obsidian-board` | Update a kanban board |
| `/obsidian-ingest` | Ingest a document into the vault |
| `/obsidian-synthesize` | Synthesize multiple sources into one note |
| `/obsidian-visualize` | Create a visual representation |
| `/obsidian-export` | Export vault content |
| `/obsidian-init` | Initialize vault structure |

---

## Automated Agents

Autonomous agents that run outside interactive sessions.

| Agent | Schedule | What it does | Log |
|-------|----------|-------------|-----|
| Nightly consolidation | 10pm daily | Propagates PostCompact summaries, updates active work notes, checks orphans | `/tmp/obsidian-claude-nightly.log` |
| Weekly review | 6pm Friday | Cross-session patterns, North Star alignment, uncaptured wins | `/tmp/obsidian-claude-weekly.log` |
| Vault health | 9pm Sunday | Structural audit — broken links, stale notes, frontmatter gaps | `/tmp/obsidian-claude-health.log` |
| PostCompact hook | On context compaction | Silently propagates session summary to vault | Runs via `obsidian-bg-agent.sh` |
| Morning briefing | Remote agent | Granola + Gmail + Slack DMs/mentions → Jira sync → Slack summary with vault-pending items | `trig_01HWnacKCbmmY3oDitKZhUCP` |
