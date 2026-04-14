# My Second Brain OS

*Anthony Giliberti · April 2026*

I spent a long time trying to make note-taking stick. The problem was never the tools — it was that no system connected what I knew, what I did each day, and what I was working on into something that actually built over time.

So I built one. This is what I built and why it works for me.

---

## The three ideas it's built on

Everything in my system comes from three thinkers whose work I combined:

**[Nick Milo's AIOS](https://www.youtube.com/@nickmilo)** — the idea that your notes vault needs an orientation layer. A small folder that tells any AI (or any person) who you are, how the vault is structured, and what it can do. Three files: `me.md`, `vault-map.md`, `skill-map.md`. Every AI conversation starts by reading these. You never re-explain your context.

**[Matthias Hilse's ForeverNote](https://www.myforevernotes.com)** — one file per calendar date, forever. `april-14.md` holds every April 14 I've ever recorded, stacked by year. My morning briefing, meetings, journal, and habits all build up in one file throughout the day — not assembled all at once. Five years from now, opening that file shows me everything from that date across every year.

**A three-bucket knowledge base** — inspired by Nick Milo's ideaverse: everything routes to Atlas (what I know), Calendar (what happened), or Efforts (what I'm working on). Drop a file in the inbox, the AI routes it. Meeting notes fan out across all three automatically.

---

## What a day actually looks like

My morning starts with a briefing that writes itself into that day's ForeverNote — weather, tasks from Reminders, events from my calendar, a quote of the day. By the time I open Obsidian it's already there.

When I finish a meeting I export the Apple Notes transcript and drop it in my inbox. A small CLI tool I wrote ([brain](https://github.com/ajgiliberti2/second-brain)) routes it automatically — it creates a calendar entry for today, updates the person's page in my knowledge base, and links it to any relevant projects. I don't decide where it goes.

Throughout the day, an iOS Shortcut prompts me to journal. It reads a pool of questions I've written (organized by day of the week, refreshed monthly by AI) directly from iCloud — no server, no API call — and records my answer as a file in the inbox. That gets picked up and appended to the day's note.

At the end of the day, `april-14.md` holds everything: weather, tasks, meetings with their notes, my journal entry, and habit tracking. Next April 14 it gets a new section. The file never moves.

---

## The AI layer

I run everything locally. The routing, ingesting, and page-writing is handled by Gemma running on my Mac via [Ollama](https://ollama.ai). No meeting note, journal entry, or personal detail ever leaves my network.

The system is deliberately AI-agnostic though. The vault is plain markdown. The CLI can point at any OpenAI-compatible endpoint. If I switch models tomorrow, nothing changes. The vault survives any tool change — that's the only design principle that matters long term.

---

## What I've learned

The thing that made this click was understanding that AI shouldn't be the system — it should be a tool the system uses. My vault is useful without AI. AI just makes the routing and ingesting faster so I actually do it.

The orientation layer (AIOS) is underrated. The reason most AI note workflows feel broken is that you re-explain your context every conversation. When the vault holds that context in files the AI reads first, every interaction starts from the right place.

And ForeverNote solved something I didn't know I was fighting: the blank page. My daily note isn't blank when I open it — it already has structure and content that arrived throughout the morning. I'm filling in gaps, not starting over.

---

## If you want to build something similar

The vault structure and CLI are open source. The framework is tool-agnostic — Obsidian, VS Code, or any markdown editor works. Local LLM or cloud API, your choice.

→ [second-brain](https://github.com/ajgiliberti2/second-brain) — the `brain` CLI (Python, MIT)

The best starting point is `me.md`. Fill in who you are and how you work. Everything else builds from that.

---

*Built on the work of [Nick Milo](https://www.youtube.com/@nickmilo), [Matthias Hilse](https://www.myforevernotes.com), and [Andrej Karpathy](https://karpathy.ai). MIT license.*
