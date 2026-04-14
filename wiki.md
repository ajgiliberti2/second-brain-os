---
layout: default
title: The Wiki
nav_order: 4
---

# The Wiki — Your Knowledge Base

The wiki is the AI-assisted layer of your vault. It routes, ingests, and organizes content so you don't have to decide where everything goes.

---

## The Three Buckets

All content routes to one of three namespaces:

### 🗺️ Atlas — What You Know
Permanent reference knowledge: concepts, people, domains, decisions, frameworks. The kind of content that doesn't expire — it just gets richer over time.

Examples: a person page for a colleague, a concept page for a technology, a domain overview for a field you work in.

### 📅 Calendar — What Happened
Time-indexed content: daily notes, meeting notes, briefings, journal entries. Organized by date, not topic. The Calendar is a record of lived experience.

Examples: today's ForeverNote, a meeting with a colleague, a log of a project milestone.

### 🎯 Efforts — What You're Working On
Active projects and initiatives. Status-driven: Active, On Hold, or Complete. Efforts are the bridge between knowledge (Atlas) and time (Calendar).

Examples: a project you're running, a goal you're working toward, an initiative you're leading.

---

## The Inbox

Content enters the vault through a single point: `inbox/`.

Drop any file there — a `.md` note, a `.txt` export, a `.pdf` — and the `brain` CLI routes and ingests it automatically:

```bash
brain process-inbox
```

The AI reads the content, decides which bucket it belongs in, writes the appropriate pages, and archives the source file. For rich content like meeting notes, it fans out across multiple buckets simultaneously — one meeting creates a calendar entry, updates the relevant person's Atlas page, and links to any active Efforts.

---

## The `brain` CLI

[`brain`](https://github.com/ajgiliberti2/llm-wiki) is a small Python CLI that powers the wiki layer. It's the only piece of code in the system.

```bash
brain process-inbox          # route and ingest everything in inbox/
brain ingest file.md --ns atlas  # ingest a specific file into a namespace
brain query "what did I discuss with X?" --ns calendar
brain config --default-ns atlas
```

### AI Backend

By default `brain` uses [Ollama](https://ollama.ai) running locally — no data leaves your machine. You can point it at any OpenAI-compatible endpoint by setting `OLLAMA_URL` in your environment.

```bash
# Local (default)
brain config --model gemma4:e4b

# Any OpenAI-compatible endpoint
export OLLAMA_URL=https://api.openai.com/v1
brain config --model gpt-4o
```

### AI Authorship Tagging

Every page the AI writes gets tagged automatically:

```yaml
tags: [ai-generated]
```

And a 🤖 marker in the content. Human-authored content is never tagged. The distinction matters — you always know what was written for you vs. by you.

---

## Routing Logic

The router uses the vault's `schema.md` files — one per bucket — to decide where content belongs. You can tune routing by editing the schema. The router also recognizes cross-cutting content and fans it out across multiple buckets without you having to specify.

Meeting notes always fan out. The router knows this.
