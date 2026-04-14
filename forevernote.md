---
layout: default
title: ForeverNote
nav_order: 5
---

# ForeverNote — The Daily Container

ForeverNote is a daily note pattern with one rule that changes everything: **one file per calendar date, forever.**

Each year's content stacks inside the same file as a new section. April 13 from 2025 and April 13 from 2026 live in `april-13.md` together, separated by year headers. The file grows; the filename never changes.

---

## The Structure

```
# April 13

## 2026

### 🌤️ Weather
### ✅ Tasks
### 📅 Today's Events
### 📰 News
### 💬 Quote of the Day
### 📓 Journal
### 💪 Habits
### 📝 Meetings
```

Each section is filled by a different source, at a different time of day. No single workflow needs to produce the whole file.

---

## Built Incrementally

This is the key idea: the ForeverNote isn't generated all at once. It builds up throughout the day as content arrives.

- **6am** — weather, quote, word of the day drop into inbox
- **Morning** — your task list and calendar events arrive via iOS Shortcut
- **After a meeting** — Krieger ingests the meeting note and appends it under `### 📝 Meetings`
- **Midday** — an iOS Shortcut prompts you for a journal entry and saves it to inbox
- **Evening** — you fill in habits directly in Obsidian

Each piece arrives independently and gets appended to the right section. The file accumulates. You never stare at a blank page.

---

## Year-Stacking

Five years from now, opening `april-13.md` shows you every April 13 you've recorded. Not in a separate archive — right there in the same file, stacked by year.

```
# April 13

## 2026
...this year's content...

## 2025
...last year's content...
```

This creates natural longitudinal context. What were you working on this week last year? Open the file and scroll up.

---

## Meetings Live Here Too

Meeting notes don't live in a separate meetings folder. They live in the ForeverNote for the day the meeting happened, under `### 📝 Meetings`. If you had three meetings on April 13, all three stack under that section.

The meeting content is also fanned out to Atlas (people pages) and Efforts (project pages) — but the canonical time-indexed record lives in the Calendar ForeverNote.

---

## Journal Prompts

The `### 📓 Journal` section uses a rotating prompt — a different question each day of the week, drawn from a pool that refreshes monthly. The prompt arrives as a file in your inbox via iOS Shortcut, is ingested by the brain CLI, and written into the journal section. You fill in your answer directly in Obsidian.

The prompt pool lives in `AIOS/skills/journal-prompts.md` — a plain markdown file you can edit anytime. The iOS Shortcut reads it directly from iCloud with no server involved.

---

## Why "Forever"

Most daily note systems create a note for today, then abandon it. ForeverNote inverts this: the file is permanent, the content is cumulative, and every year you use it the file becomes more valuable.

The name comes from the commitment: this file lives for as long as you maintain the vault. You don't archive it, you don't delete it. You just keep writing.

---

*The ForeverNote pattern was created by [Matthias Hilse](https://www.myforevernotes.com). The implementation here adapts it for AI-assisted, inbox-driven vaults.*
