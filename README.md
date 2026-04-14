# My Second Brain is an AI Operating System — Here's How I Built It

*Anthony Giliberti · April 2026*

---

I've been experimenting with AI tools for knowledge work long enough to know the pattern. You ask a question, you get a confident answer, you move on. A week later you ask a related question and get a slightly different answer. You paste in a document for context, get a great summary, then close the tab and lose it forever.

The deeper problem isn't the model. It's that every conversation starts cold. The AI doesn't know what you already know, what you decided last month, or what you're actively working on. You end up re-explaining your context every single time — or worse, you stop bothering and just trust whatever it generates.

That's not a fundamental limitation of AI. It's a limitation of how we're using it.

---

## The Core Idea: A Knowledge OS

A Knowledge OS is a structured vault that you build and maintain, with AI as the reasoning and synthesis layer on top of it. The vault is the memory. The AI is the thinking. You bring the judgment.

The roles are clear:
- **Your job:** Curate the vault. Ingest good sources. Keep the structure clean. Define how things connect.
- **AI's job:** Read the vault — not its training data. Synthesize from what you've actually captured. Answer based on your context, not generic knowledge.

Every answer you get is grounded in files you've actually read, reviewed, and organized. When the model is wrong, you know why — because the vault doesn't have the right source yet. That's a very different relationship than trusting a black box.

---

## The Architecture

The vault lives in iCloud, opened in Obsidian. The AI layer is Claude, running with a `CLAUDE.md` at the vault root that points it to the orientation layer first.

```
second-brain/
├── AIOS/
│   ├── me.md
│   ├── vault-map.md
│   ├── skill-map.md
│   └── skills/
├── atlas/
│   ├── people/
│   ├── concepts/
│   └── domains/
├── calendar/
├── efforts/
└── inbox/
    └── archive/
```

Two things make the vault work that aren't obvious from the folder names:

The `CLAUDE.md` at the root contains one line: `Read AIOS/me.md.` That one line kicks off a chain — me.md links to vault-map, which links to skill-map, which links to every skill. Any AI reading this is fully oriented before it does anything.

The three-bucket routing rule: every piece of content belongs in exactly one of three places — **Atlas** (what I know), **Calendar** (what happened), **Efforts** (what I'm working on). When content crosses buckets — like a meeting note that touches a person, a date, and a project — it fans out to all of them in one pass.

---

## me.md — The AI's Briefing on Me

Every session starts with the AI reading this file. It's my professional identity document: who I am, what I do, how I work, what I care about, and what's on my plate right now.

The working preferences section matters most. I've written out how I want to be communicated with:

> *Direct and concise — skip preamble, get to the point.*  
> *Treat me like a thinking partner, not a tool.*  
> *Skip filler phrases like "Great question" or "Certainly" — just help.*

This file is read-only for AI. Only I edit it. It's the one file in the vault that represents me, not the system — and that distinction matters.

---

## Skills — Reusable Process Definitions

Instead of re-prompting the same workflows from scratch, I've defined reusable skills. Each one is a Markdown file in `AIOS/skills/` with a trigger phrase, a step-by-step process, and edge case handling.

**Ingest** — triggered when I drop a file in `inbox/`. The AI reads the content, routes it to the right bucket, writes structured pages, and archives the source. Meeting notes fan out: a calendar entry gets created, the person's atlas page gets updated, and any active efforts get linked. One file in, multiple organized pages out.

**Query** — triggered when I ask a question about vault content. The AI reads all relevant pages, synthesizes from my actual captured knowledge rather than training data, and shows its reasoning. Critically: it's instructed to say "the vault doesn't have this" rather than fall back on generic answers.

**ForeverNote** — the daily note framework (see below). One skill defines the structure all daily content writes into.

**Journal Prompts** — a rotating pool of questions by day of week. The AI reads this file directly to generate daily prompts. The pool refreshes monthly.

---

## ForeverNote — The Daily Container

*Framework by [Matthias Hilse](https://www.myforevernotes.com)*

One file per calendar date, forever. `april-14.md` holds every April 14 I've ever recorded, stacked by year. The filename never changes — next year it gets a new `## 2027` section inside the same file.

```
# April 14

## 2026

### 🌤️ Weather
### ✅ Tasks
### 📅 Today's Events
### 💬 Quote of the Day
### 📓 Journal
### 💪 Habits
### 📝 Meetings
```

The key is that this note builds incrementally throughout the day — not assembled all at once. Weather and tasks arrive in the morning. A meeting note drops in at 10am and gets appended automatically. A journal prompt comes through an iOS Shortcut at noon. By end of day the file is complete without me ever opening a blank page.

Five years from now, opening `april-14.md` shows me everything from that date across every year. It's not an archive — it's longitudinal context.

---

## A Real Example: Ingesting a Meeting Note

I finished a mentor session with a colleague and exported the Apple Notes transcript into my inbox. The file contained attendees, discussion topics, and action items.

I ran `brain process-inbox`. Here's what happened:

- A **calendar entry** was created for April 13 with the meeting notes appended under `### 📝 Meetings` — preserving everything else already in that day's ForeverNote
- A **people page** was created in `atlas/people/` capturing the colleague's role, focus areas, and what we discussed
- The **action item** (colleague to send a white paper) was extracted and surfaced

That took about 30 seconds. The work instance of this approach handled a 40-page threat intelligence report the same way — source page, gap analysis, presentation outline — in about 20 minutes of conversation. The difference between that and doing it manually isn't speed. It's that the output is grounded in the actual vault context, not generic analysis.

---

## Principles Behind the Design

**Ground truth is sacred.** Source pages must be faithful to the actual source material. The moment you let conclusions contaminate the source layer, the vault loses its value. Keep them separate — sources are what you know, artifacts are what you've reasoned from sources.

**Consistency enables memory.** Every page has frontmatter: `up` (breadcrumb parent), `related`, `created`, `tags`. AI-generated pages are tagged `ai-generated` and marked with 🤖. Human-authored pages are never tagged. The AI navigates by these consistently — which means you can trust its synthesis across sessions.

**Define two skills first: Ingest and Query.** You don't need the full skill set on day one. Those two are enough to start building the knowledge base. Add ForeverNote when you're ready for the daily note layer.

**Log operations, not just content.** Every ingest goes through `inbox/`. This creates a record of what entered the vault, when, and what was created from it. The log is what the briefing skill reads to catch you up.

**The AI is better than you expect — once you give it something real.** An AI working from a well-curated vault is qualitatively different from an AI reasoning from nothing. You can't outsource the curation. You can ask for help with it. But you are the knowledge curator. You bring the judgment.

---

## How to Build Your Own

You don't need my exact stack. The vault is plain markdown — Obsidian, VS Code, iA Writer, anything works. The AI can be Claude, ChatGPT, Gemini, or a local model via Ollama. The tool-agnostic design is intentional: the vault outlasts any specific AI.

**Start here:**

1. **Create `AIOS/me.md`** — Write your professional identity document. Role, domain, team, working preferences, current focus. Be specific about how you want the AI to interact with you. This is the highest-leverage file in the entire vault.

2. **Create `AIOS/vault-map.md`** — Define the folder structure, the three buckets, file naming conventions, and the inbox flow. The AI will follow these if they're documented clearly.

3. **Define Ingest and Query as your first two skills.** Don't try to build the whole system at once. Two skills and five ingested documents will teach you more than planning ever will.

4. **Process three to five documents you actually care about.** Run the ingest skill on real content and process based on what you learn. The first pass reveals what the schema is missing.

5. **Add ForeverNote when ready.** Once the knowledge base has some weight, add the daily note layer. The two systems reinforce each other — daily notes link to atlas pages, atlas pages get richer as meetings get ingested.

**Common mistakes to avoid:**

- Don't make every page a stub. If something isn't worth a full page, don't create it. Stub proliferation is the fastest way to build a junk vault.
- Don't skip the log. If you don't track what entered the vault, the briefing skill has nothing to read.
- Don't trust your conclusions on source pages. Keep sources clean. Conclusions go in artifacts.
- Don't try to automate everything on day one. Understand the loop manually before you build automation around it.

---

## What I've Learned

The biggest surprise was how much the discipline of building the system changed my own thinking — not just the AI's output.

Writing a good source page forces you to actually understand the document you're processing. The process of cross-linking forces you to make connections you'd missed. The process of separating sources from conclusions — keeping them in different places — turns into something like a coding discipline. You can't let them mix.

The AI is better at this work than I expected. But only because I gave it something real to work with. You can't outsource the curation. You can ask for help with it — and I have — but you are the knowledge curator. You can't outsource the judgment.

That's the principle Karpathy illustrated and the one I've found to be true: the model isn't the interesting part. The sources are. The same model in front of a well-curated vault is a completely different tool than the same model reasoning from nothing.

---

## Closing

AIOS is not a product, a framework, or a startup idea. It's a practice — a way of working that treats your professional knowledge as a first-class asset worth organizing. The AI makes the practice sustainable. Without it, the curation overhead is too high. With it, the overhead drops to the point where maintaining the vault is faster than not maintaining it.

If you're a knowledge worker who finds yourself re-explaining context, re-doing analysis, or losing track of what you've concluded and why — this is worth trying.

**The value is in the memory. The AI is the thinking. You bring the judgment.**

---

*The thought process here is inspired by [Nick Milo's AIOS Framework](https://www.youtube.com/@nickmilo) and [Matthias Hilse's ForeverNote](https://www.myforevernotes.com). The specific implementation is my own. Inspired by [Andrej Karpathy's](https://karpathy.ai) approach to publishing thinking in progress.*

*The vault structure and `brain` CLI are open source: [second-brain-os](https://github.com/ajgiliberti2/second-brain-os) · [second-brain](https://github.com/ajgiliberti2/second-brain)*
