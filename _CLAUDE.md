---
date: 2026-05-26
description: "Vault operating manual for Claude — routing rules, naming conventions, auto-save behavior, and excluded structures for the obsidian-mind vault"
ai-first: true
type: vault-manifest
tags: [meta, operating-manual]
---

## For future Claude
Primary vault operating manual. Read this before any vault operation. Overrides skill defaults where specified.

---

# Vault Operating Manual — Spencer Sutton

## Identity

Read [[CRITICAL_FACTS]] first (always loaded). Read [[SOUL]] for voice, values, and working style before writing or strategy work.

## Vault Structure

| Folder | Purpose |
|--------|---------|
| `brain/` | Operating protocols, North Star, memory index, decisions, patterns, gotchas |
| `work/active/` | Current projects (Navigator pipeline, Apollo Studio, Nova, Q2 OKRs) |
| `work/1-1/` | 1:1 meeting notes named `<Person> YYYY-MM-DD.md` |
| `work/archive/YYYY/` | Completed work by year |
| `work/incidents/` | Incident docs |
| `work/meetings/` | Inbox for raw meeting exports — process with `/om-intake` |
| `org/people/` | One note per person — internal team + key external contacts |
| `org/teams/` | Team notes |
| `perf/Brag Doc.md` | Running log of wins |
| `perf/competencies/` | One note per competency |
| `reference/Navigator/Hospitals/` | One note per Navigator prospect/customer |
| `reference/` | Product sheets, prompts, reference docs |
| `templates/` | Note templates with YAML frontmatter |
| `thinking/` | Scratchpad — promote findings, then delete |

## Naming Conventions

- 1:1 notes: `<Person> YYYY-MM-DD.md`
- Work notes: descriptive title, no date prefix unless date-specific
- Hospital notes: `<Hospital Name>.md`
- Person notes: `<Full Name>.md`

## Frontmatter — Minimum Required

```yaml
---
date: YYYY-MM-DD
description: "one-line summary"
tags: [note-type]
---
```

Hospital notes use: `status`, `contact`, `email`, `next-meeting` fields.
Person notes use: `role`, `company`, `relationship` fields.

## Key Files

- Dashboard: [[Home]]
- Active projects: [[work/Index]]
- Pipeline: [[Navigator Hospital Pipeline]]
- Protocols: [[Jira Management Agent]], [[brain/Writing & Document Co-Authoring Protocol]]
- Identity: [[SOUL]], [[CRITICAL_FACTS]]
- Memory index: [[Memories]]

## Routing Rules

These rules override any default paths from obsidian-second-brain commands or background agents.

| Content type | Destination |
|---|---|
| Navigator prospect update | `reference/Navigator/Hospitals/<Hospital>.md` — append under `## Update — YYYY-MM-DD` |
| Internal 1:1 meeting | `work/1-1/<Person> YYYY-MM-DD.md` |
| Active project update | `work/active/<Project>.md` |
| New person (internal team) | `org/people/<Name>.md` |
| New person (external prospect/contact) | `org/people/<Name>.md` + link from hospital note |
| Decision | `work/Index.md` Decisions Log + relevant project note |
| Win / recognition | `perf/Brag Doc.md` |
| Action item | `work/active/<Project>.md` as `- [ ]` |
| Blocker | `work/active/<Project>.md` under `## Blockers` |
| Scratchpad / draft / reasoning | `thinking/YYYY-MM-DD-topic.md` — delete after promoting findings |
| LinkedIn post (draft) | `reference/linkedin/drafts/YYYY-MM-DD-slug.md` |
| LinkedIn post (approved/published) | `reference/linkedin/samples/YYYY-MM-DD-slug.md` — used for voice calibration |
| Sanity test case (approved) | `reference/Navigator/Cases/approved/YYYY-MM-DD-{disease}-{slug}.md` |
| Sanity test case (pending/generated) | `reference/Navigator/Cases/pending/YYYY-MM-DD-{disease}-{slug}.md` |
| Clinical guideline (local hospital protocol) | `reference/Navigator/Cases/guidelines/local/{name}.md` |
| Clinical guideline (national society) | `reference/Navigator/Cases/guidelines/national/{name}.md` |
| Clinical concept (cross-functional theory) | `reference/Navigator/Cases/guidelines/concepts/{name}.md` |
| Case style guide | `brain/Case Style Guide.md` — written by `/om-case-analyze` |

## Excluded Structures

These folders and patterns do NOT exist in this vault. Do not create them.

| Excluded | Use instead |
|---|---|
| `Daily/` or daily notes | No daily note structure. Skip any step that writes to a daily note. |
| `People/` | Use `org/people/` |
| `Projects/` | Use `work/active/` |
| `Ideas/` | Use `thinking/` for scratchpad; promote to `work/active/` or `brain/` when durable |
| `Dev Logs/` | Not applicable — this is a sales/GTM vault, not an engineering repo |
| `Boards/` or kanban views | Not applicable |
| `Wiki/` | Not applicable |

If an obsidian-second-brain command or background agent tries to create any of these, skip that step and use the correct destination from the Routing Rules table above.

## Auto-Save Behavior

Save to vault whenever Spencer mentions:
- A deal update, prospect reply, or meeting outcome
- A decision made or direction set
- A new person introduced
- A commitment made or received
- A win or recognition

Ask before saving only if the target note is genuinely ambiguous.

## Priority Order

IRX Navigator > Apollo > Nova > Sales > Partnerships > Research

When surfacing items, ordering tickets, or writing briefings — always in this order.

## Writing Standard

Apply stop-slop rules at all times. See `~/.claude/CLAUDE.md` for full spec. No adverbs, no em dashes, no passive voice, no filler. First person, sounds like Spencer.

## Private Folders

None designated. All vault content is Spencer's work context.
