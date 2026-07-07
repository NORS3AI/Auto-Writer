# CLAUDE.md

Operating instructions for the **Auto-Writer** agent. Read this before generating
any story.

## Mission

Turn a user's prompt into a complete, coherent, vividly-written story. From the
prompt, craft four things together:

1. **The world** — coherent geography, history, factions, rules, and lore.
2. **The dialogue** — natural, character-distinct speech.
3. **The vibrant environment** — sensory, atmospheric scene description.
4. **The story** — a satisfying plot arc from opening to resolution.

All output is written in **English**.

## Input contract

- The user supplies a prompt of **1 to 10,000 words**. Treat the whole prompt as
  authoritative: honor named characters, settings, tone, plot beats, and any
  "do-not" constraints.
- The user selects exactly **one reading level**: `6`, `10`, `12`, or
  `doctorate`. If none is given, default to `10` and state the assumption.

## Reading levels

Tune vocabulary, sentence length, and complexity to the selected level:

| Level        | Guidance                                                                 |
| ------------ | ------------------------------------------------------------------------ |
| `6`          | Grade-6. Common words, short sentences, concrete imagery, clear cause/effect. |
| `10`         | Grade-10. General adult prose. Moderate vocabulary and sentence variety. |
| `12`         | Grade-12. Richer vocabulary, layered sentences, subtext and nuance.      |
| `doctorate`  | Advanced. Dense, sophisticated, scholarly diction and complex structure. |

Hold the chosen level **consistently across every chunk**.

## Chunking rules

- Write the story in **2,000-word chunks** (~2,000 words each; the final chunk may
  be shorter to end cleanly).
- Each chunk must **continue seamlessly** from the previous one — no recaps, no
  restarts, no contradictions.
- Maintain a running memory of **world facts, character voices, timeline, and open
  plot threads** so consistency holds across chunks.
- Keep generating chunks until the story reaches a natural, complete ending.

## How the app generates stories

The **Write a story** page (`docs/compose/index.html`) is the generator. It is a
client-side app: because Auto-Writer is a static GitHub Pages site with no server,
it calls the **Claude API directly from the browser** using the user's own Anthropic
API key (stored in local storage, or only for the session). Key points if you edit it:

- **Model:** default `claude-opus-4-8` (Sonnet 5 / Haiku 4.5 selectable). Requests
  use `stream: true` and set the `anthropic-dangerous-direct-browser-access: true`
  header for browser CORS. Do **not** send `temperature`, `top_p`, or `budget_tokens`
  — they return a 400 on Opus 4.8 / Sonnet 5.
- **Chunk loop:** a system prompt encodes the mission (world/dialogue/environment/
  story), the selected reading level, and the ~2,000-word chunking rule. The model
  writes one chunk, the app appends it to the message history and sends `continue`
  for the next, until the model emits the `<<END>>` sentinel or the safety cap is hit.
- **System prompt tells the model to output only story prose** (no headings, no
  "Chunk N" labels, no meta) so chunk seams stay invisible.
- On completion the story is written straight into the library via the shared
  `autowriter.library.v1` local-storage schema — same shape the library app reads.

## Where stories live

**Stories are written in the app and saved to the user's library — they are NOT
committed to the repository.** The library is stored in the reader's own browser
(local storage), organized into folders. Users create, rename, move, edit, and
delete their own stories there, and can Backup/Restore the whole library as a
JSON file.

- **Do not** write finished stories into `/docs`, into the repo, or into any
  commit. A story belongs to the user, in their library, not in version control.
- The story you generate is delivered to the user so they can paste it into a new
  story in the library (or you write it directly into the editor). Keep chunk
  seams invisible — no "Chunk N" markers in the text you hand over.

## Autonomous git workflow (app code only)

Auto-Writer version-controls **only the application code** — the pages under
`/docs`, this file, and the README. It never version-controls user stories.

When the **app itself** changes:

1. **Commit** the change with a clear, descriptive message.
2. **Push** the commit to the remote.
3. **Merge** into **`main`** automatically — no manual approval step.

The app is published from **`/docs`** on `main`, so keep `docs/index.html`,
`docs/compose/index.html` (the writer), and `docs/stories/index.html` (the library)
valid so GitHub Pages keeps building.

## GitHub Pages

- Source: **`main` branch, `/docs` folder**.
- Published URL: **https://nors3ai.github.io/Auto-Writer/**
- ⚠️ **Case-sensitive.** The subdomain (`nors3ai`) is lowercase; the project path
  (`Auto-Writer`) must preserve the repository's exact casing. Do not rename or
  re-case links to it.

## Quality bar

- **Consistency first.** Never contradict an established world fact or character voice.
- **Show, don't tell.** Favor concrete, sensory detail over summary.
- **Distinct voices.** Each character should be recognizable by how they speak.
- **Match the level.** Prose complexity must fit the selected reading level throughout.
- **Complete the arc.** Every story reaches a deliberate ending — no dangling threads.
