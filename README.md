# Auto-Writer

**Auto-Writer** turns a single prompt into a complete, richly-imagined story. From
your idea it crafts the **world**, the **dialogue**, the **vibrant environment**, and
the **story** itself — writing it in the app and saving it to **your library**, where
you organize, edit, and manage your stories. Your writing stays in your browser; only
the app's own code is version-controlled on GitHub.

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

Open the **Write a story** page, paste a prompt, pick a reading level, and Auto-Writer
**writes the whole story for you** — you watch the prose stream in live. It generates
the story in **2,000-word chunks**, each continuing seamlessly from the last, keeping
world facts, character voices, and plot threads consistent from the first chunk to the
final one. This keeps quality high over long works and lets the story grow to any length
without losing coherence. The story ends on its own when the arc resolves, then saves
straight to your library.

### Powered by Claude, straight from your browser

Auto-Writer is a **static site with no server**, so the app calls the
[Claude API](https://console.anthropic.com/settings/keys) directly from your browser
using **your own Anthropic API key**. The key is stored only on your device (or only
for the session, if you choose) and is used solely for these requests. Get a key at
[console.anthropic.com](https://console.anthropic.com/settings/keys). The default model
is Claude Opus 4.8; Sonnet 5 and Haiku 4.5 are also selectable.

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

## Your library — where stories live

Stories are created and written **in the app**, then saved to **your library**.
The library lives in **your browser** (local storage) — it is **not** uploaded to
the repository, and finished stories are never committed to the code. In the
library you can:

- **Create folders** and rename or delete them,
- **Add stories**, and rename, **move between folders**, edit, or delete them,
- **Edit the story text** in a built-in editor (title, reading level, and body),
- **Backup / Restore** the whole library as a JSON file for safekeeping.

Only the **application's own code** (the pages under `/docs`) is version-controlled
on GitHub. Your writing stays with you.

## Quick start

1. Open **Write a story** and paste your prompt (1–10,000 words).
2. Pick a reading level: **6**, **10**, **12**, or **doctorate**.
3. Add your Anthropic API key (stored on your device) and click **Write the story**.
4. Watch it stream in; it's saved to **your library** automatically when it finishes.
5. Organize stories into folders and edit them any time in the library.

## Repository layout

```
Auto-Writer/
├── README.md            # This file
├── CLAUDE.md            # Operating instructions for the Auto-Writer agent
└── docs/                # GitHub Pages site (source: main /docs) — app code only
    ├── index.html       # Landing page — https://nors3ai.github.io/Auto-Writer/
    ├── compose/
    │   └── index.html   # The writer — prompt → streamed story (calls the Claude API)
    └── stories/
        └── index.html   # Your library app (folders + story editor, browser-stored)
```

## GitHub Pages setup

The site is served from the **`main`** branch, **`/docs`** folder.

To (re)enable it in the repository: **Settings → Pages → Build and deployment →
Source: _Deploy from a branch_ → Branch: `main` / folder: `/docs`**.

The published URL is **https://nors3ai.github.io/Auto-Writer/** — remember, it is
case-sensitive.
