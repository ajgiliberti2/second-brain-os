---
up: "[[AIOS/me]]"
related: "[[AIOS/skill-map]]"
---

> [[AIOS/me|me.md]] · [[AIOS/skill-map|skill-map.md]]

# Vault Map

> The authoritative guide to this vault's structure. Any AI reads this before writing anything.

## Folder Structure

```
vault/
├── AIOS/               ← orientation layer (this folder)
│   ├── me.md           ← identity, read-only for AI
│   ├── vault-map.md    ← this file
│   ├── skill-map.md    ← skills and agent roster
│   └── skills/         ← individual skill definitions
├── atlas/              ← knowledge (people, concepts, domains)
├── calendar/           ← time (daily notes, meetings)
├── efforts/            ← projects (active work)
├── inbox/              ← drop files here for AI routing
│   └── archive/        ← processed files land here
└── x/                  ← templates and scratch
    └── templates/
```

## The Three Buckets

| Bucket | Purpose | File naming |
|---|---|---|
| `atlas/` | Permanent knowledge | `people/name.md`, `concepts/topic.md` |
| `calendar/` | Time-indexed notes | `month-day.md` (e.g. `april-14.md`) |
| `efforts/` | Active projects | `project-name.md` |

## Inbox Flow

1. Drop any `.md`, `.txt`, or `.pdf` into `inbox/`
2. Run `brain process-inbox`
3. AI routes to the correct bucket, writes pages, archives source

## Note Conventions

- All cross-references use Obsidian wikilinks: `[[folder/page|Display Text]]`
- Frontmatter on every page: `up` (parent), `related`, `created`
- AI-generated pages are tagged `ai-generated` and marked with 🤖
- Human-authored pages are never tagged
