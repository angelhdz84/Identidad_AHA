# AGENTS.md — Identidad_AHA

## What this repo is

Single-document meta-repo. The only source is `filosofia-stack-ahaguilera.md` — it defines the AHAguilera brand identity, offline-first stack (Alpine + Dexie + CryptoJS + Tailwind/DaisyUI), and code-generation rules for AI agents.

No code, no build, no tests, no CI. This repo is read by agents to bootstrap specs for apps built in *other* repos.

## Key facts

- **No app code lives here** — this is a philosophy/brand reference document
- The file is the source of truth for: stack compliance rules (§5.1), anti-pattern catalog (§5.2), visual tones (§6.2), code patterns (§7), and pipeline flow (§4)
- No git, no package.json, no config files of any kind

## What agents should do

- Before generating code for any AHAguilera-branded app, read `filosofia-stack-ahaguilera.md` §5 (Stack Compliance) and §7 (Code Patterns)
- Use the spec-creator skill flow when asked to create a new app spec: read this file for brand/stack context, then produce `specs/[app].md`
- All UI, comments, docs, and variables must be in Spanish (§8.1)
- No CDNs, no ES6 `import`, no `fetch()`, no `type="module"` — enforced at the stack level (§5.1)

## Brand assets

- `brand/guidelines.md` — Visual identity guide (colors, typography, logo usage, voice & tone)
- `brand/palette.json` — Machine-readable color tokens (surface, text, accent, semantic, light-theme)
- `brand/logo-icon.svg`, `logo-wordmark.svg`, `logo-full.svg` — SVG logo variants
- `brand/favicon/` — Favicon + apple-touch-icon + site.webmanifest
- `brand/guia-estilos.html` — Interactive style guide (HTML)
- `colores.txt` — Quick hex reference: `171614`, `CFF434`, `EAF4F5`, `024653`, `07D16E`

## Brand colors (quick reference)

| Token | Hex | Use |
|-------|-----|-----|
| Surface | `#171614` | Dark background |
| Accent primary | `#CFF434` | CTAs, links, highlights (≤10% of surface) |
| Text primary | `#EAF4F5` | Text on dark |
| Surface teal | `#024653` | Featured sections, tags |
| Accent secondary | `#07D16E` | Success, secondary badges |

## Commands

None — no build, test, lint, or deploy targets exist.
