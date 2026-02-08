# CLAUDE.md

## Project Overview

**Claude Descodificado** is a single-page static website (in Portuguese) that serves as an interactive tutorial teaching users how to create "artifacts" in Claude AI. It is hosted on GitHub Pages at `claude.descodificado.com.br`.

## Tech Stack

- **HTML5** / **CSS3** / **Vanilla JavaScript** — no frameworks, no build tools, no external dependencies
- **GitHub Pages** — hosting and deployment (push-to-deploy)
- **Git** — version control

## Repository Structure

```
/
├── index.html          # Entire application (HTML + embedded CSS + JS)
├── CNAME               # GitHub Pages custom domain config
├── topo-claude.png     # Header banner image
├── rodape-claude.png   # Footer banner image
└── CLAUDE.md           # This file
```

This is a flat repository with no subdirectories. The entire site lives in a single `index.html` file (~660 lines) with inline `<style>` and `<script>` blocks.

## Architecture

### Single-File Structure (`index.html`)

The HTML file is organized as:

1. **`<style>` block** — ~300 CSS rules covering reset, theming, animations, component styles, and responsive design
2. **`<body>` content** — semantic HTML with 5 collapsible tutorial sections inside a `.container` (max-width 900px)
3. **`<script>` block** — 3 vanilla JS functions for interactivity

### Content Sections

| Section | Topic |
|---------|-------|
| Passo 1 | How to request an artifact from Claude |
| Passo 2 | What happens when Claude creates an artifact |
| Passo 3 | How to copy the artifact code |
| Passo 4 | How to save as an HTML file |
| Dicas Extras | Tips and common mistakes |

### JavaScript Functions

- `toggleSection(id)` — expand/collapse tutorial sections
- `markComplete(step, event)` — toggle step completion status
- `getOriginalIcon(step)` — return the emoji icon for each step

### Design System

- **Theme**: Dark mode with glassmorphism (backdrop-filter blur)
- **Primary colors**: Cyan `#06b6d4`, Light Cyan `#22d3ee`, Sky Blue `#0ea5e9`
- **Background**: Dark slate gradient (`#0a1628` → `#0f172a` → `#1e293b`)
- **Text**: Slate `#94a3b8` on dark backgrounds
- **Animations**: `fadeIn` (0.8s), `slideUp` (0.5s), hover scale/glow effects
- **Alert styles**: 6 color variants (blue, purple, green, yellow, red, teal)
- **Font**: Segoe UI / system sans-serif stack

## Development Workflow

### No Build Step Required

This is a zero-config static site. Edit `index.html` directly — no compilation, bundling, or preprocessing needed.

### Local Development

Open `index.html` in a browser, or serve it locally:

```bash
python3 -m http.server 8000
# Then visit http://localhost:8000
```

### Deployment

Push to the `main` branch on GitHub. GitHub Pages automatically deploys the site to `claude.descodificado.com.br` (configured via the `CNAME` file).

### No Testing, Linting, or CI/CD

There are no test suites, linters, formatters, or CI pipelines configured.

## Conventions for AI Assistants

### Language

- All user-facing content is in **Brazilian Portuguese (pt-BR)**. Maintain this language for any content changes.
- Code comments and technical identifiers (CSS classes, JS function names) are in English.

### Coding Style

- All CSS is inline in the `<style>` tag — do not create separate `.css` files unless explicitly requested.
- All JS is inline in the `<script>` tag — do not create separate `.js` files unless explicitly requested.
- CSS class names use kebab-case (e.g., `.section-content`, `.alert-blue`).
- JS functions use camelCase (e.g., `toggleSection`, `markComplete`).
- No external CDN links or dependencies — keep the site fully self-contained.

### Visual Design

- Maintain the dark theme with cyan/teal accent colors.
- Use the existing glassmorphism pattern (`backdrop-filter: blur()`, semi-transparent backgrounds) for new components.
- Ensure responsive design — the site must work well on mobile devices.

### Images

- Banner images (`topo-claude.png`, `rodape-claude.png`) are large files (~3MB each). Avoid adding more large unoptimized images.

### Git

- The repository has a simple linear commit history.
- Commit messages should be concise and descriptive.
