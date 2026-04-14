---
layout: home
title: Home
nav_order: 1
---

# Second Brain OS

A personal knowledge system built on plain markdown files, a small CLI tool, and any AI you choose. Fork it, fill in your name, and start dropping notes.

[Fork the vault template on GitHub](https://github.com/ajgiliberti2/second-brain-os){: .btn .btn-primary .fs-5 .mr-2 }
[Get the brain CLI](https://github.com/ajgiliberti2/second-brain){: .btn .fs-5 }

---

## What you get

A folder structure that actually holds up — organized into three buckets that cover everything:

| Bucket | What goes here |
|---|---|
| `atlas/` | Knowledge — people, concepts, domains, reference |
| `calendar/` | Time — daily notes, meetings, journal entries |
| `efforts/` | Projects — active work, goals, initiatives |

Drop any file into `inbox/` and the `brain` CLI routes it to the right bucket automatically. Meeting notes fan out across all three — calendar entry, person page in atlas, project update in efforts — in one pass.

---

## The three ideas this is built on

**AIOS** (by [Nick Milo](https://www.youtube.com/@nickmilo)) — A small folder inside your vault that orients any AI to your system. Three files: who you are (`me.md`), how the vault works (`vault-map.md`), what skills exist (`skill-map.md`). Any AI reads these first. You never re-explain your context.

**ForeverNote** (by [Matthias Hilse](https://www.myforevernotes.com)) — One file per calendar date, forever. `april-14.md` holds every April 14 you've ever recorded, stacked by year. Your morning briefing, meetings, and journal all live in one file per day, built up as the day goes by — not assembled all at once.

**The Wiki** — A three-bucket knowledge base with an AI router. Drop files in `inbox/`, run `brain process-inbox`, find organized pages in your vault. Works with any AI — local or cloud.

---

## Get started in 3 steps

### 1. Fork the vault template

Click **Fork** on the [second-brain-os repo](https://github.com/ajgiliberti2/second-brain-os) — the `vault/` folder is your starting point. Open it in [Obsidian](https://obsidian.md) or any markdown editor.

Fill in `vault/AIOS/me.md` with your own context. That's the only file you must edit before the system knows who you are.

### 2. Install the brain CLI

```bash
git clone https://github.com/ajgiliberti2/second-brain
cd second-brain && pip install -e .
```

Point it at your vault:

```bash
export WIKI_HOME=/path/to/your/vault
```

### 3. Drop something in the inbox and run it

```bash
echo "Meeting with Alex — topics: Q2 roadmap, hiring. Action: Alex sends proposal by Friday." \
  > ~/vault/inbox/alex-meeting.md

brain process-inbox
```

Check your vault. There's a calendar entry for today and a person page for Alex in `atlas/people/`. That's the loop.

---

## Choose your AI

The system is AI-agnostic. The `brain` CLI talks to any Ollama-compatible endpoint.

**Local (no data leaves your machine):**
```bash
# Install Ollama — https://ollama.ai
ollama pull gemma3:4b
# brain uses http://localhost:11434 by default
```

**Cloud API:**
```bash
export OLLAMA_URL=https://api.openai.com/v1
export OLLAMA_API_KEY=sk-...
brain config --model gpt-4o-mini
```

Swap models anytime. Nothing in your vault changes.

---

## The daily note

Each day gets one file: `calendar/april-14.md`. It builds up throughout the day:

```markdown
# April 14

## 2026

### 🌤️ Weather
Sunny, 68°F

### ✅ Tasks
- [ ] Finish Q2 proposal

### 📓 Journal
*What's the one thing that would make this week a success?*

### 💪 Habits
⏰ Wake: 6:30am
💪 Workout: ✓

### 📝 Meetings
**10am — Alex Chen**
Topics: Q2 roadmap, hiring plan
Action: Alex to send proposal by Friday
```

Next year, April 14 gets a new `## 2027` section in the same file. The file grows. The filename never changes.

---

## What this is not

- Not an app. No subscription. No account.
- Not dependent on any specific AI. Swap the model, the vault stays the same.
- Not a replacement for Obsidian (or any editor). It's just folders and markdown files.
- Not finished. It's a living system — yours to extend.

---

*Built by Anthony Giliberti. MIT license. Standing on the shoulders of [Nick Milo](https://www.youtube.com/@nickmilo), [Matthias Hilse](https://www.myforevernotes.com), and [Andrej Karpathy](https://karpathy.ai).*
