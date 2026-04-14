# Second Brain OS

A personal knowledge framework built on three ideas: [Nick Milo's AIOS](https://www.youtube.com/@nickmilo), [Matthias Hilse's ForeverNote](https://www.myforevernotes.com), and a three-bucket knowledge base. Works with any AI tool. No app required — just markdown files.

**To set it up:** copy the prompt below and paste it into Claude, ChatGPT, Gemini, or any AI you use. It will build the framework for you.

---

## The Prompt

````
I want to set up a personal knowledge system called Second Brain OS. It's built on three frameworks. Please help me create it step by step.

---

## Framework 1: AIOS (Orientation Layer)
*Credit: Nick Milo (youtube.com/@nickmilo)*

Create a folder called AIOS/ inside my vault with these files:

**AIOS/me.md** — Ask me: my name, role, location, how I like to work, my current focus, and what tools I use (calendar, tasks, editor). Fill in my answers. This file is read-only for AI — only I edit it.

**AIOS/vault-map.md** — Document the vault structure we're building:
- atlas/ — permanent knowledge (people, concepts, domains)
- calendar/ — time-indexed notes (daily notes, meetings)  
- efforts/ — active projects and goals
- inbox/ — drop files here, AI routes them
- inbox/archive/ — processed files land here
- AIOS/ — this orientation layer
Include file naming conventions, note format rules, and inbox flow.

**AIOS/skill-map.md** — An index of skills in this vault. Start with:
- ForeverNote (Framework) — the daily note pattern
- Meeting Notes (Workflow) — routes meetings across all three buckets
- Journal Prompts (Data) — rotating daily prompts

**AIOS/skills/forevernote.md** — Document the ForeverNote pattern (see Framework 2 below).

**AIOS/skills/journal-prompts.md** — Create a pool of 7-10 journal prompts for each day of the week. Monday: intention-setting. Tuesday: challenge. Wednesday: mid-week check-in. Thursday: progress. Friday: reflection. Saturday: personal. Sunday: preparation. Format each day as `## Monday` with `- prompt` bullet lines.

At the root of the vault, create **CLAUDE.md** (or the equivalent for your AI tool) containing one line: `Read AIOS/me.md.`

---

## Framework 2: ForeverNote (Daily Container)
*Credit: Matthias Hilse (myforevernotes.com)*

One file per calendar date, forever. The file is named `month-day.md` (e.g. `april-14.md`) and lives in calendar/. Every year stacks as a new `## YYYY` section inside the same file — the filename never changes.

Each day's file follows this section structure:
```
# Month Day

## YYYY

### 🌤️ Weather
### ✅ Tasks
### 📅 Today's Events
### 📰 News
### 💬 Quote of the Day
### 📓 Journal
### 💪 Habits
### 📝 Meetings
```

The note builds incrementally throughout the day — different sections filled by different sources at different times. It is never assembled all at once.

Create today's ForeverNote for me now using this structure.

---

## Framework 3: Three-Bucket Knowledge Base

Create the three bucket folders with schema files:

**atlas/schema.md** — Route here for permanent knowledge: people, concepts, technologies, decisions, domains. Not time-indexed.

**calendar/schema.md** — Route here for time-indexed content. File naming: `month-day.md`. The ForeverNote pattern applies.

**efforts/schema.md** — Route here for active projects and goals. Status: Active, On Hold, or Complete.

The routing rule: when content touches more than one bucket (e.g. a meeting involves a date, a person, and a project), write to all relevant buckets in one pass. Meeting notes always fan out to all three.

---

## After Setup

Once the structure is created, here's how to use it day to day:

- **Drop anything into inbox/** — a meeting note, an article, a voice memo transcript, any text. Ask your AI to route and ingest it.
- **Each morning** — ask your AI to create today's ForeverNote and fill in the weather, tasks, and events sections.
- **After a meeting** — paste your notes and ask your AI to update the calendar entry, create or update the person's atlas page, and link to any relevant efforts.
- **Journaling** — open AIOS/skills/journal-prompts.md, find today's day of the week, pick a prompt, and write your answer in the Journal section of today's ForeverNote.
- **To ask questions** — "what did I discuss with [name]?", "what are my active efforts?", "what was I working on last month?" — your AI reads the vault and answers.

The vault is plain markdown. It works with Obsidian, VS Code, iA Writer, or any text editor. The AI is a tool the system uses — not the system itself.
````

---

*Framework by Anthony Giliberti. Built on the work of [Matthias Hilse](https://www.myforevernotes.com), [Nick Milo](https://www.youtube.com/@nickmilo), and [Andrej Karpathy](https://karpathy.ai). MIT license.*
