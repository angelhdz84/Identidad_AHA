# Implementation Plan: Landing Page AHAguilera

> **Spec**: `docs/2026-06-16-landing-ahaguilera-design.md`
> **Fecha**: 2026-06-16
> **Stack**: HTML + Tailwind CSS local + Alpine.js

---

## Phase 1: Project Setup

**Goal**: Estructura de archivos + dependencias locales

1. Crear directorio `landing/`
2. Copiar/crear assets:
   - `assets/css/tailwind.min.css` — Tailwind CSS compilado
   - `assets/css/daisyui.min.css` — DaisyUI 5
   - `assets/css/bootstrap-icons.css` — Bootstrap Icons
   - `assets/js/libs/alpine.js` — Alpine.js
3. Copiar logos de `brand/` a `landing/brand/`
4. Crear `index.html` con estructura base (head, meta, script tags)

**Deliverable**: Estructura lista, `index.html` abre sin errores en `file://`

---

## Phase 2: Core Layout + CSS Variables

**Goal**: Variables de marca, reset, utilidades base

1. Definir CSS custom properties (colores de `brand/palette.json`)
2. Configurar Tailwind config para colores de marca
3. Estilos base: body, tipografía (Inter + JetBrains Mono via Google Fonts local o system-ui)
4. Clases utilitarias: `.fade-in`, `.slide-up`, `.slide-left`, `.slide-right`
5. Nav sticky con backdrop-blur

**Deliverable**: Página con colores correctos, nav funcional, sin contenido

---

## Phase 3: Hero Section

**Goal**: Hero con video/gradiente + headline + CTAs

1. Hero full-screen con video de fondo (o gradiente animado como fallback)
2. Logo AHAguilera completo centrado
3. Headline + subheadline
4. 2 CTAs (WhatsApp + scroll)
5. Scroll indicator animado
6. Animaciones fade-in delay progresivo

**Deliverable**: Hero completo y visualmente impactante

---

## Phase 4: Content Sections (1-6)

**Goal**: Secciones de contenido principales

1. **§2 Problema** — 3 pain points con iconos
2. **§3 Solución** — Grid de beneficios + quote
3. **§4 Apps** — Grid 2x2 de cards mock
4. **§5 Cómo funciona** — Stepper visual 3 pasos
5. **§6 Stack técnico** — Logo grid + progress bars
6. **§7 Precios** — 3 cards de precio

**Deliverable**: 6 secciones funcionales con contenido

---

## Phase 5: Content Sections (7-12)

**Goal**: Secciones restantes

1. **§8 Comparativa** — Tabla offline vs tradicional
2. **§9 Portafolio** — Code snippet con syntax highlighting
3. **§10 Testimonios** — 3 cards de testimonios
4. **§11 FAQ** — Acordeón con Alpine.js
5. **§12 Sobre ti** — Bio + skills
6. **§13 CTA final** — WhatsApp + Email
7. **§14 Footer** — Links + copyright + palette bar

**Deliverable**: Landing completa con todo el contenido

---

## Phase 6: Interactivity

**Goal**: Alpine.js interactions

1. Toggle idioma ES/EN (store + localStorage)
2. Nav active section highlight (Intersection Observer)
3. FAQ acordeón (x-show + transitions)
4. Modal de apps (click en "Ver más")
5. Hamburger menu mobile

**Deliverable**: Toda la interactividad funcionando

---

## Phase 7: Animations + Scroll Effects

**Goal**: Scroll-triggered animations

1. Intersection Observer setup para todas las secciones
2. Parallax sutil en hero
3. Stepper lines animation
4. Tabla comparativa stagger animation
5. Progress bars animation (stack section)
6. `prefers-reduced-motion` check

**Deliverable**: Scroll effects suaves y funcionales

---

## Phase 8: Responsive

**Goal**: Mobile + tablet

1. Breakpoints: mobile < 768px, tablet 768-1024px
2. Grids a 1 columna en mobile
3. Stepper vertical en mobile
4. Tabla comparativa como cards en mobile
5. Nav hamburger en mobile
6. Touch targets ≥ 44x44px

**Deliverable**: Landing responsive en todos los breakpoints

---

## Phase 9: Polish + Validation

**Goal**: QA final

1. Validar colores contra `brand/palette.json`
2. Verificar contraste WCAG AA (4.5:1)
3. Probar en Chrome, Firefox, Edge
4. Probar `file://` (sin servidor)
5. Verificar que no hay CDNs, imports ES6, fetch()
6. Minificar CSS/JS si aplica
7. Crear `site.webmanifest` para PWA básica

**Deliverable**: Landing lista para deploy

---

## Execution Order

```
Phase 1 → Phase 2 → Phase 3 → Phase 4 → Phase 5 → Phase 6 → Phase 7 → Phase 8 → Phase 9
```

Cada phase se ejecuta en orden. El usuario puede revisar después de cada phase.

## Estimated Size

- `index.html`: ~1500-2000 líneas
- CSS inline (Tailwind + custom): ~200 líneas
- JS inline (Alpine + Intersection Observer): ~300 líneas
- Total: ~2000-2500 líneas en 1 archivo
