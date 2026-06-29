# AGENTS.md — Identidad_AHA

## What this repo is

Brand identity meta-repo for **AHAguilera** (freelance dev, offline-first stack). The single source of truth is `filosofia-stack-ahaguilera.md` — defines brand philosophy, stack rules, code patterns, and the 5-phase pipeline.

**Also ships real code:** `landing/` is a production static site deployed to GitHub Pages. It is NOT just a meta-repo.

## Landing: estado actual (Enfoque A — Cálido-Tech)

La landing sigue el **Enfoque A** (Cálido-Tech): balancea profesionalismo, artesanal, destaca y tech/futurista. Diseño dual-mode:

| Modo | Fondo | Secciones |
|------|-------|-----------|
| Beige (#F5F0EB) | Cálido, claro | Hero, Valor, Cómo funciona, FAQ, Footer |
| Carbón (#171614) | Oscuro, tech | Nav flotante, Apps, IA Jutia, Precios, Stack, Comparativa, Sobre mí, CTA |
| Gradiente orgánico | Beige→Carbón y viceversa | Transiciones suaves entre secciones |

**Acento único**: `#CFF434` (lime) — funciona sobre ambos modos, máximo 10% del área visual.

## Cambios recientes

- ✅ **Calculadora eliminada** (Jun 2026) — Se removió la calculadora de precios para simplificar la experiencia. Los precios ahora se muestran directamente en las cards de cada plan.
- ✅ **6 testimonios implementados** — Carrusel con 2 cards por página, transición suave, 6 testimonials en total.
- ✅ **Avatar actualizado** — Se agregó `brand/avatar_aha.webp` como avatar personal en Sobre Mí.
- ✅ **Stack redesign** (Jun 2026) — Flip cards 3D reemplazadas por grid 3-col simétrica. Sección Partners eliminada (contenido integrado en Stack como tagline strip + footer pills). Se añadió h2 + subtitle siguiendo la jerarquía visual de las demás secciones oscuras. Consistencia visual corregida (se usaban tokens de modo claro en sección oscura).

## Secciones de la landing (orden actual)

1. **Nav dual-glass** — logo redondo, links, toggle ES/EN, hamburguesa móvil
  2. **Hero oscuro** — headline, subheadline, 2 CTAs, badge .exe+.apk, stats (tagline now single line: "Apps offline-first que parecen magia.")
3. **Valor beige** — 3 cards con iconos + bloque comparativo "Software normal vs Cómo trabajo yo"
4. **Apps oscuro** — Grid catálogo (InventarioPRO, FacturaExpress, ClienteSeguro, GastosDiarios)
5. **IA Jutia oscuro** — Mini IA offline-first, perfiles Lite/Full, bloque comparativo competencia
6. **Precios oscuro** — 3 planes (Lite $49, Standard $99⭐, Custom $199+) con IA Jutia incluida
7. **Cómo funciona beige** — 3 pasos + timeline vertical
8. **Stack técnico** — Eyebrow + h2 + subtitle + tagline strip (LOCAL · MILLONES · OPEN SOURCE) + 6 cards grid 3-col con iconos, descripción, download stats y tags + footer pills (Open Source, 100% local, Actualización vitalicia, Sin vendor lock-in)
9. **Comparativa offline-first** — tabla vs SaaS tradicional
10. **FAQ beige** — acordeón con 7 preguntas (incluye "¿Qué es IA Jutia?")
11. **Sobre mí oscuro** — bio, skills, badge IA Jutia
12. **CTA Final oscuro** — WhatsApp + Email
13. **Footer beige** — logo, links sociales, tagline

## Logotipo

- **Archivo único**: `landing/brand/logotipo.jpg` — circular (`border-radius: 50%`)
- Usado como: logo en nav y footer, favicon del sitio (formato JPEG), OG Image, Twitter Card image
- Tamaños: nav 2rem, footer 2.5rem
- Favicon declarado como: `<link rel="icon" href="./brand/logotipo.jpg" type="image/jpeg">`

## WhatsApp

- Número real: **+5355944628** (Cuba)
- Reemplazado en 25 enlaces (24 landing + 1 brand/identidad-ahaguilera.html)
- Cada app del catálogo tiene su propio texto predefinido (ej: `?text=Quiero%20InventarioPRO`)

## IA Jutia en la landing

- Sección dedicada oscura entre Apps y Precios
- Dos perfiles: **Lite** (búsqueda FlexSearch + predicciones) y **Full** (+ingesta documentos + QA extractivo)
- Bloque comparativo: "Lo que la competencia no puede decir" (4 statements)
- Pricing refleja IA incluida: Lite en plan Lite, Full en Standard y Custom

## Stack grid (tecnologías principales)

6 cards en grid 3-col con: icono, nombre, descripción con iconos inline, download stats + tags. Footer pills con 4 badges de posicionamiento. El contenido de la sección Partners anterior se integró como tagline strip y pills del footer.

| Tecnología | Icono | Descripción | Estadística | Tag |
|-----------|-------|-------------|-------------|-----|
| Alpine.js | snow2 | Interfaz reactiva 100% local. Sin servidor. | 2M+/sem | Sin servidor |
| Dexie.js | database | BD en navegador. Tus datos no se van. | 500K+/sem | Sin backend |
| Tailwind CSS | wind | Estilos responsive compilados. Sin CDN. | 15M+/sem | Sin CDN |
| DaisyUI | palette | Componentes listos: botones, tabs, modales. | 3M+/sem | Sin framework extra |
| Bootstrap Icons | bootstrap-reboot | 2,000+ iconos vectoriales gratuitos. | Gratuito | Sin licencia |
| CryptoJS | lock | Cifrado AES-256. Solo tú tienes la llave. | 10M+/sem | Sin terceros |

## Key identity sources (read these first)

| File | What it defines |
|------|----------------|
| `filosofia-stack-ahaguilera.md` | Manifesto (§1), stack choices (§2), Lite/Full profiles (§3), pipeline (§4), compliance rules (§5.1), anti-patterns (§5.2), code patterns (§7), Spanish mandate (§8.1) |
| `brand/guidelines.md` | Logo usage, colors, typography, voice & tone |
| `brand/palette.json` | Machine-readable color tokens (surface, text, accent, semantic, light-theme) |
| `brand/identidad-ahaguilera.html` | Documento completo de identidad de marca (11 secciones, auto-contenido, sin CDN) |
| `landing/brand/logotipo.jpg` | Logotipo único (JPEG, circular) — logo, favicon y OG image |
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

## Encoding (critical)

- **PowerShell `Set-Content` sin `-Encoding UTF8` corrompe acentos y emojis** — usar SIEMPRE `-Encoding UTF8`
- Los parciales (`_head.html`, `_body*.html`) son editados por el `edit` tool que maneja UTF-8 correctamente
- **`index.html` se genera concatenando parciales**: `Get-Content -Encoding UTF8 _head.html, _body1.html, _body2.html, _body3.html | Set-Content -Encoding UTF8 index.html`
- Si ves caracteres raros (ó→Ã³, í→Ã­, etc.), regenerar index.html con UTF-8 explicito

## File map

| Path | Purpose |
|------|---------|
| `filosofia-stack-ahaguilera.md` | Brand + stack source of truth |
| `DESIGN.md` | **AuthKit — not AHAguilera.** Probably leftover; ignore for AHAguilera work |
| `landing/DESIGN.md` | Design system Enfoque A — tokens dual-mode, componentes, animaciones, microcopy |
| `landing/` | Production landing page (deployed) |
| `landing/index.html` + `_head.html`, `_body1.html`, `_body2.html`, `_body3.html` | Landing page partials + generated index (re-generate con `-Encoding UTF8`) |
| `landing/brand/logotipo.jpg` | Logotipo único (JPEG, circular) |
| `brand/` | Visual assets (guidelines, palette, favicon SVGs legacy, identidad-ahaguilera.html) |
| `brand/identidad-ahaguilera.html` | Documento identidad de marca (11 secciones, auto-contenido, sin CDN) |
| `brand/favicon/` | Favicon legacy (ICONO_OK.svg, apple-touch-icon.svg — ya no referenciados) |
| `brand/favicon/ICONO_OK.svg` | SVG original del icono (reemplazado por logotipo.jpg como logo/favicon) |
| `specs/landing-v2.md` | Spec funcional de la landing (actualizar con Enfoque A) |
| `docs/landing-aha-sell.md` | Estrategia de venta: IA Jutia, argumentos cliente, catálogo 13 apps, guiones WhatsApp |
| `docs/` | Design docs, implementation plans |
| `.superpowers/`, `+/` | Agent session data (gitignored — ignore) |
