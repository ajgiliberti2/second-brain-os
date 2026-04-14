---
layout: default
title: Philosophy
nav_order: 2
---

# Philosophy

## Tool-Agnostic by Design

Every component of Second Brain OS is a plain markdown file or a standard file system operation. The AI layer is pluggable — it sits on top, not underneath.

The system was built and tested using a fully local LLM ([Ollama](https://ollama.ai) running Gemma). It works equally well with the Claude API, GPT-4, or any model that can read a prompt and return structured text. When you swap models, nothing in your vault changes.

This matters because AI tools change fast. The model you use today may not be the model you use in two years. Your notes shouldn't depend on which one wins.

---

## Local-First Optional

The reference implementation is intentionally local-first:

- The vault lives in iCloud (or any folder you choose)
- The AI runs on your machine via Ollama — no data leaves your network
- The `brain` CLI is a Python script you install locally

You can swap in any cloud API if you prefer speed over privacy. The architecture doesn't care. The only thing that matters is that your AI can read a prompt and return JSON.

**Why offer local at all?** Because some content — meeting notes, personal journal entries, health data — shouldn't leave your machine. The local path makes that possible without sacrificing AI assistance.

---

## Three Buckets, Not Folders

Most note-taking systems collapse under their own weight because they don't enforce a routing discipline. Files go wherever feels right at the time, and six months later nothing is findable.

Second Brain OS enforces three buckets from the start:

| Bucket | What goes here |
|---|---|
| **Atlas** | Knowledge — concepts, people, domains, reference |
| **Calendar** | Time — daily notes, meeting notes, events |
| **Efforts** | Projects — active work, goals, initiatives |

Every piece of content belongs in exactly one bucket. When you're not sure, the AI router decides. When you disagree with the router, you move the file. Simple.

---

## The Vault Survives Everything

Plain markdown. No database. No proprietary format. No app required.

The vault worked before AI assisted it. It will work after whatever AI tool you're using today is discontinued, acquired, or changed. The AIOS orientation layer is just more markdown — it tells any future tool what the vault is and how to navigate it.

This is the only design principle that matters long-term: **your notes belong to you, in a format that outlasts any tool.**

---

## Standing on Shoulders

This system is built on the thinking of others:

- **Nick Milo** — AIOS orientation layer, Atlas/Calendar/Efforts model, the idea that your notes system needs a control plane
- **Matthias Hilse** ([myforevernotes.com](https://www.myforevernotes.com)) — the ForeverNote pattern: one file per date, forever, years stacking inside
- **Andrej Karpathy** — the wiki-as-public-thinking ethos: write for yourself, share anyway
- **The Obsidian community** — wikilink conventions, the vault as a first-class concept
