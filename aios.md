---
layout: default
title: AIOS
nav_order: 3
---

# AIOS — The Orientation Layer

Every vault needs a control plane: a small set of files that tell any AI or tool who you are, how the vault is structured, and what it's allowed to do on your behalf. That's AIOS.

It's not an app or a service. It's a folder — `AIOS/` — sitting inside your vault.

---

## The Three Files

### `me.md` — Identity
Who you are, how you work, what context any AI needs to assist you well. Roles, preferences, communication style, working patterns. Written by you, read-only for all AI tools.

This file answers: *"Who am I working with?"*

### `vault-map.md` — Structure
The authoritative guide to how the vault is organized: folder structure, file naming conventions, note types, Obsidian syntax rules, inbox flow, and protected paths. Any AI reading this knows how to navigate and write to the vault correctly.

This file answers: *"How does this vault work?"*

### `skill-map.md` — Capabilities
An index of all defined skills the AI can execute on your behalf, plus a roster of any agents in your system and what each handles. References individual skill files in `AIOS/skills/`.

This file answers: *"What can be done here and by whom?"*

---

## Skills

Skills live in `AIOS/skills/`. Each is a markdown file that defines either a **Framework** (structural pattern) or a **Workflow** (specific process).

Examples:
- `forevernote.md` — Framework: the daily note container pattern
- `briefing.md` — Workflow: assembles morning content into a ForeverNote
- `meeting-notes.md` — Workflow: ingests meeting exports across vault buckets
- `journal-prompts.md` — Data: prompt pool read directly by iOS Shortcuts

The skill files are the source of truth for how tasks are performed. When you change a skill, every tool that reads it updates automatically — no deploy, no config change.

---

## Privacy Rules

AIOS establishes hard rules about what AI can and cannot do:

- `me.md` — read-only for all AI, human edits only
- `calendar/` — personal, never routed to external APIs
- Sensitive domains — never routed externally

These rules live in `skill-map.md` and are read by any agent before acting.

---

## Why This Works

Most people's note systems have no orientation layer. Every AI conversation starts cold — you re-explain your context every time. AIOS solves this by making your context a file the AI reads before doing anything else.

The `CLAUDE.md` at the vault root contains one line: `Read AIOS/me.md.` That's enough — the rest chains from there.
