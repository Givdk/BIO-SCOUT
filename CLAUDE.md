# CLAUDE.md — BIO-SCOUT

This file provides guidance for AI assistants working in this repository.

## Project Overview

**Bio-Scout DK** is an early-stage citizen science web app that gamifies nature exploration in Denmark. The goal is to bridge biodiversity data collection with modern outdoor lifestyles through a sleek, tech-first interface.

Current state: **Alpha / proof-of-concept** — a single static HTML file deployed via GitHub Pages.

## Repository Structure

```
BIO-SCOUT/
├── index.html      # Entire application — the only source file
├── README.md       # Project description and feature checklist
├── gitignore       # Git ignore rules (note: no leading dot)
└── CLAUDE.md       # This file
```

There is no build system, no package manager, no backend, no database, and no test infrastructure. Everything lives in `index.html`.

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Markup | HTML5 (`lang="da"`, Danish) |
| Styling | Tailwind CSS via CDN (`https://cdn.tailwindcss.com`) |
| Logic | Vanilla JavaScript (inline `<script>` tag) |
| Hosting | GitHub Pages (static file deployment) |

No npm, no bundler, no transpilation — changes to `index.html` are immediately live.

## Current Application State (`index.html`)

- Dark background (`bg-slate-900`), full-screen centered layout
- `BIO-SCOUT ALIVE` heading in cyan (`#00E5FF`) with neon glow
- Circular camera button (`w-24 h-24 rounded-full`) with SVG camera icon
- Danish label: "Tryk for at teste kamera" (Press to test camera)
- Button click triggers `alert("Kamera-systemet aktiveres nu!")` — a placeholder stub

The camera access, mission board, and other features listed in README are **not yet implemented**.

## Development Workflow

### Making changes
Edit `index.html` directly. Open it in a browser to preview. No build step needed.

### Running locally
```bash
# Any static file server works, e.g.:
python3 -m http.server 8080
# Then open http://localhost:8080
```

### Git conventions
- Commit messages are written in English
- Typical format: `Verb + subject` (e.g., "Add camera access handler")
- Main branch: `main`
- Feature/task branches follow the pattern: `claude/<description>-<id>`

### Deploying
Push to `main` — GitHub Pages serves the site automatically from the repo root.

## Code Conventions

Since the project is pure HTML/JS/Tailwind with no tooling:

- **Tailwind classes**: Use utility classes directly in HTML. Tailwind CDN is loaded at runtime, no purging.
- **Custom colors**: Cyan accent is `#00E5FF`. Keep consistent with existing neon/dark aesthetic.
- **JavaScript**: Keep inline in a single `<script>` tag at the bottom of `<body>` for now. Use `const`/`let`, arrow functions, and modern DOM APIs.
- **Language**: UI text is in Danish. Code, comments, and commit messages are in English.
- **No external JS libraries** beyond Tailwind CDN unless absolutely necessary.

## Key Design Decisions

- **No framework** — deliberately minimal; the project is exploring ideas before committing to a stack.
- **Mobile-first** — intended for use outdoors on phones. Tailwind's responsive utilities and viewport meta tag are configured.
- **Dark mode only** — `bg-slate-900` base with cyan (`#00E5FF`) as the primary accent.
- **No build step** — lowers the barrier for contribution; anyone can open the file and edit.

## Planned Features (not yet implemented)

From README and commit history:
- Live camera access (scanner interface for identifying species)
- Dynamic mission board (gamified biodiversity challenges)
- Image capture feature

## Gitignore Notes

The gitignore file is named `gitignore` (without a leading dot) but is tracked as a regular file. The `.gitignore` functionality is handled by the actual git configuration. The listed exclusions are:
```
.DS_Store
node_modules/
dist/
*.log
```

## What AI Assistants Should Know

1. **The entire app is `index.html`** — all edits happen there.
2. **No tests exist** — there is nothing to run after making changes.
3. **No linter or formatter** — follow existing style (2-space indentation, Tailwind utilities).
4. **Avoid adding complexity prematurely** — this is an MVP; keep changes minimal and focused.
5. **Keep Tailwind via CDN** until there is a clear reason to introduce a build step.
6. **Danish UI text** — if adding visible text elements, write them in Danish.
7. **Branch**: develop on `claude/add-claude-documentation-mJnDe`, push to that branch.
