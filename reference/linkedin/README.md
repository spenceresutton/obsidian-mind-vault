---
date: 2026-05-26
description: "LinkedIn content store — approved post samples for voice calibration and in-progress drafts"
tags: [reference, linkedin, content]
---

# LinkedIn Content

Two subfolders:

- `samples/` — approved and published posts. These are the voice training data for `/linkedin`. The more samples here, the more accurately the tool matches Spencer's voice.
- `drafts/` — in-progress posts. Status: draft until approved.

## Usage

Run `/linkedin` from any Claude session to enter the interactive post generation workflow.

The tool scans recent Granola notes, 1:1s, and hospital pipeline updates for post-worthy angles, presents a brief, then drafts in Spencer's voice.

When you approve a post, save it here as a sample. The tool reads the 3 most recent samples at each session start for voice calibration.

## Voice Pillars

Posts draw from these angles (derived from vault context):
- What clinicians actually need vs. what tech assumes
- Real implementation friction (IT security, EHR, clinical workflow)
- AI design decisions — why the glass-box approach matters
- Patterns from hospital conversations (anonymized)
- The gap between AI demos and clinical adoption
