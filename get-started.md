---
layout: default
title: Get Started
nav_order: 6
---

# Get Started

Second Brain OS has two parts: the **vault** (your markdown files) and the **brain CLI** (the AI routing layer). You can set up the vault without the CLI — it's useful on its own. Add the CLI when you're ready for AI-assisted inbox routing.

---

## 1. Set Up the Vault

Clone or fork this repo as a starting point, or create the folder structure manually:

```
second-brain/
├── CLAUDE.md               ← one line: Read AIOS/me.md
├── AIOS/
│   ├── me.md               ← fill this in: who you are, how you work
│   ├── vault-map.md        ← how the vault is structured
│   ├── skill-map.md        ← what skills/agents exist
│   └── skills/
│       ├── forevernote.md
│       ├── briefing.md
│       ├── meeting-notes.md
│       └── journal-prompts.md
├── atlas/
│   ├── schema.md
│   └── index.md
├── calendar/
│   ├── schema.md
│   └── index.md
├── efforts/
│   ├── schema.md
│   └── index.md
├── inbox/
│   └── archive/
└── x/
    └── templates/
```

Open the vault in [Obsidian](https://obsidian.md) (or any markdown editor). Fill in `AIOS/me.md` with your own context.

---

## 2. Install the brain CLI

Requires Python 3.9+.

```bash
git clone https://github.com/ajgiliberti2/llm-wiki
cd llm-wiki
pip install -e .
```

Point it at your vault:

```bash
export WIKI_HOME=/path/to/your/second-brain
brain config --default-ns atlas
```

---

## 3. Choose Your AI Backend

**Option A — Local (recommended for privacy)**

Install [Ollama](https://ollama.ai) and pull a model:

```bash
ollama pull gemma3:4b        # fast, good quality
ollama pull llama3.1:8b      # larger, better reasoning
```

The brain CLI uses Ollama at `http://localhost:11434` by default. No config needed.

**Option B — Cloud API**

Set your endpoint and model:

```bash
export OLLAMA_URL=https://api.openai.com/v1
export OLLAMA_API_KEY=sk-...
brain config --model gpt-4o-mini
```

Any OpenAI-compatible endpoint works.

---

## 4. Drop Something in the Inbox

Create a note and drop it in `inbox/`:

```
Meeting with Alex — 2026-04-14

Attendees: Alex Chen
Topics: Q2 roadmap, hiring plan
Action items: Alex to send proposal by Friday
```

Run the CLI:

```bash
brain process-inbox
```

Watch it route, ingest, and archive. Check your vault — there should be a new calendar entry and a people page for Alex.

---

## 5. Start Your First ForeverNote

Create `calendar/april-14.md`:

```markdown
---
tags: [daily-note]
---

# April 14

## 2026

### 📓 Journal

*Monday prompt:* What's the one thing that would make this week a success?

### 💪 Habits
⏰ Wake: 
😴 Sleep: 
💪 Workout: 
```

That's it. Add to it throughout the day. Drop meeting notes in the inbox and let the brain CLI append them automatically.

---

## What's Next

- Read the [AIOS](aios) docs to understand the orientation layer
- Read the [ForeverNote](forevernote) docs to understand the daily note pattern
- Customize `AIOS/me.md` with your own context
- Edit `AIOS/skills/journal-prompts.md` with prompts that resonate with you
- Set up an iOS Shortcut to drop journal entries directly into inbox (guide coming soon)
