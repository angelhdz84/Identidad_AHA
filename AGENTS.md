# AGENTS.md — Identidad_AHA

## What this repo is

Brand identity meta-repo for **AHAguilera** (freelance dev, offline-first stack). The single source of truth is `filosofia-stack-ahaguilera.md` — defines brand philosophy, stack rules, code patterns, and the 5-phase pipeline.

**Also ships real code:** `landing/` is a production static site deployed to GitHub Pages. It is NOT just a meta-repo.

## Key identity sources (read these first)

| File | What it defines |
|------|----------------|
| `filosofia-stack-ahaguilera.md` | Manifesto (§1), stack choices (§2), Lite/Full profiles (§3), pipeline (§4), compliance rules (§5.1), anti-patterns (§5.2), code patterns (§7), Spanish mandate (§8.1) |
| `brand/guidelines.md` | Logo usage, colors, typography, voice & tone |
| `brand/palette.json` | Machine-readable color tokens (surface, text, accent, semantic, light-theme) |
| `brand/logo-*.svg` | Logo variants (icon, wordmark, full) |
| `colores.txt` | Quick hex: `171614`, `CFF434`, `F5F0EB`, `024653`, `07D16E` |

## Brand colors

| Token | Hex | Use |
|-------|-----|-----|
| Surface dark | `#171614` | Dark sections, CTAs |
| Accent lime | `#CFF434` | CTAs, links, highlights (≤10% of surface) |
| Canvas beige | `#F5F0EB` | Light/warm sections |
| Teal surface | `#024653` | Featured sections, tags |
| Green success | `#07D16E` | Badges, success states |

## Deploy

- **GitHub Pages** — `landing/` deploys automatically on push to `master` via `.github/workflows/deploy-pages.yml`
- No build step, no bundler — the landing is static HTML/CSS/JS opened by double-clicking `index.html`
- No package.json, no npm — all libraries are in `landing/assets/`

## Stack rules (enforced at the code level)

- No CDNs, no ES6 `import`, no `fetch()`, no `type="module"` — everything must work from `file://`
- All UI, comments, docs, and variables in Spanish (§8.1)
- Before generating code for any AHAguilera-branded app: read §5 (Stack Compliance) and §7 (Code Patterns)

## File map

| Path | Purpose |
|------|---------|
| `filosofia-stack-ahaguilera.md` | Brand + stack source of truth |
| `DESIGN.md` | **AuthKit — not AHAguilera.** Probably leftover; ignore for AHAguilera work |
| `landing/DESIGN.md` | Design system for the landing page (dual-mode beige/dark, lime accent) |
| `landing/` | Production landing page (deployed) |
| `landing/index.html` + `_head.html`, `_body*.html` | Landing page partials (assembled by agent during dev) |
| `brand/` | Visual assets (logos, favicon, guidelines, palette, style guide HTML) |
| `specs/landing-v2.md` | Spec that generated the current landing |
| `docs/` | Design docs, implementation plans |
| `.superpowers/`, `+/` | Agent session data (gitignored — ignore) |
