# Auto-Writer

**Auto-Writer** turns a single prompt into a complete, richly-imagined story. From
your idea it crafts the **world**, the **dialogue**, the **vibrant environment**, and
the **story** itself — then writes, commits, pushes, and merges the finished work to
`main` entirely on its own.

🌐 **Live site:** https://nors3ai.github.io/Auto-Writer/

> ⚠️ The Pages URL is **case-sensitive**. The subdomain (`nors3ai`) is lowercase, but
> the project path (`Auto-Writer`) preserves the repository's exact casing. Any other
> casing (e.g. `auto-writer`) will **404**.

---

## What it does

Give Auto-Writer a prompt describing what you want to read, and it will:

1. **Build the world** — geography, history, factions, rules, and lore.
2. **Voice the characters** — natural, distinct dialogue for every speaker.
3. **Paint the environment** — vivid, sensory descriptions of every scene.
4. **Tell the story** — a coherent plot with beginning, middle, and end.

The story is written in **English**.

## How it writes: 2000-word chunks

Auto-Writer generates the story in **2,000-word chunks**. Each chunk continues
seamlessly from the last, keeping world facts, character voices, and plot threads
consistent from the first chunk to the final one. This keeps quality high over
long works and lets the story grow to any length without losing coherence.

## Your input: up to 10,000 words

Your prompt can be anything from a single sentence to a **detailed brief of up to
10,000 words**. The more context you give — characters, setting, tone, plot beats,
things to avoid — the more closely the finished story matches your vision.

## Reading level

Choose the reading level that fits your audience. Auto-Writer tunes vocabulary,
sentence length, and complexity to match:

| Level          | Audience                                             |
| -------------- | ---------------------------------------------------- |
| **6**          | Grade 6 — simple vocabulary, short sentences         |
| **10**         | Grade 10 — general adult reading                     |
| **12**         | Grade 12 — richer vocabulary, layered sentences      |
| **Doctorate**  | Advanced — dense, sophisticated, scholarly prose     |

## Autonomous publishing

Auto-Writer manages its own git workflow. Once a story is complete it will:

- **Commit** the finished work with a descriptive message,
- **Push** the commit, and
- **Merge** the result into `main` — automatically, with no manual step required.

Completed stories are published to GitHub Pages from the `main` branch `/docs`
folder, so every merge updates the live site at
https://nors3ai.github.io/Auto-Writer/.

## Quick start

1. Write your prompt (1–10,000 words) describing the story you want.
2. Pick a reading level: **6**, **10**, **12**, or **doctorate**.
3. Run Auto-Writer. It generates the story in 2,000-word chunks, then commits,
   pushes, and merges to `main` on its own.
4. Read the result on the live site.

## Repository layout

```
Auto-Writer/
├── README.md      # This file
├── CLAUDE.md      # Operating instructions for the Auto-Writer agent
└── docs/          # GitHub Pages site (source: main /docs)
    └── index.html # Landing page — https://nors3ai.github.io/Auto-Writer/
```

## GitHub Pages setup

The site is served from the **`main`** branch, **`/docs`** folder.

To (re)enable it in the repository: **Settings → Pages → Build and deployment →
Source: _Deploy from a branch_ → Branch: `main` / folder: `/docs`**.

The published URL is **https://nors3ai.github.io/Auto-Writer/** — remember, it is
case-sensitive.
