# Second Brain OS

A personal knowledge operating system built on three open frameworks — for anyone who wants their notes, daily life, and AI tools to actually work together.

**→ [Read the docs](https://ajgiliberti2.github.io/second-brain-os)**

---

## What It Is

Three frameworks, one vault:

- **AIOS** — An orientation layer that tells any AI who you are, how your vault works, and what it's allowed to do on your behalf
- **The Wiki** — A three-bucket knowledge base (Atlas / Calendar / Efforts) with AI-assisted inbox routing via the `brain` CLI
- **ForeverNote** — A daily note pattern where one file per calendar date accumulates content incrementally throughout the day, forever

## Philosophy

- Tool-agnostic — works with any AI (Claude, GPT, Gemini, or a local model)
- Local-first optional — the reference implementation runs entirely on [Ollama](https://ollama.ai), no data leaves your machine
- Plain markdown — no proprietary format, no lock-in, works in any editor

## Quick Start

```bash
git clone https://github.com/ajgiliberti2/second-brain
cd second-brain && pip install -e .
export WIKI_HOME=/path/to/your/vault
brain process-inbox
```

→ [Full setup guide](https://ajgiliberti2.github.io/second-brain-os/get-started)

## Inspired By

- [Nick Milo](https://www.youtube.com/@nickmilo) — AIOS orientation layer, Atlas/Calendar/Efforts model
- [Matthias Hilse](https://www.myforevernotes.com) — ForeverNote pattern
- [Andrej Karpathy](https://karpathy.ai) — the wiki-as-public-thinking ethos

## License

MIT
