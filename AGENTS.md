# Agents

## Project Overview

This repo contains a Slidev presentation deck in `./2026-Q2-jai-dev-summit-keynote/`.

Slidev is a markdown-based slide framework built on Vite + Vue. The deck is split into sections to avoid merge conflicts.

## Slidev Skill

The official Slidev skill is installed for agent use:

```bash
# Already done — installs to .kiro/skills/slidev/ and .agents/skills/slidev/
npx skills add slidevjs/slidev --agent kiro-cli --skill slidev --yes
```

Reference docs are in `.kiro/skills/slidev/references/` — consult them for syntax, layouts, animations, components, etc.

## Dev Server

The user starts the dev server manually. The default port is **3030**.

Before making slide edits, check if the dev server is running:

```bash
lsof -i :3030 -sTCP:LISTEN
```

If nothing is listening, prompt the user:

> The Slidev dev server doesn't appear to be running on port 3030. Please start it:
> ```
> cd 2026-Q2-jai-dev-summit-keynote && yarn dev
> ```

## Commands

All commands run from `./2026-Q2-jai-dev-summit-keynote/`:

| Task | Command |
|------|---------|
| Install deps | `yarn install` |
| Start dev server | `yarn dev` (opens http://localhost:3030) |
| Build static SPA | `yarn build` |
| Export to PDF | `yarn export` |

## Deck Structure

```
2026-Q2-jai-dev-summit-keynote/
  slides.md              # headmatter + title slide + src imports only
  sections/
    01-jupyter-ai-v3.md  # 20 min — Jupyter AI v3.0 launch
    02-nb-cli.md         # 10 min — nb-cli (colleague owns)
    03-strategy.md       # 15 min — open source & DX strategy
    04-roadmap.md        # 15 min — roadmap from here
```

- `slides.md` is the entry point. It contains deck-wide config and the title slide, then imports each section via `src:`.
- Each section file starts with a section divider slide.
- Sections use `_meta` frontmatter for planning metadata (`duration`, `outline`).

## Editing Conventions

- Slides are separated by `---`
- The first frontmatter block in `slides.md` is the headmatter (deck-wide config)
- Presenter notes go in `<!-- HTML comments -->` at the end of each slide
- Theme: `seriph`
- Transition: `slide-left`
- Custom `_meta` fields are ignored by Slidev but used for planning:
  ```yaml
  _meta:
    duration: 20min
    outline:
      - Topic 1
      - Topic 2
  ```
