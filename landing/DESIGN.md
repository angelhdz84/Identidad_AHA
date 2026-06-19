# DESIGN.md — AHAguilera Landing Page v2

> **Fecha**: 2026-06-19
> **Inspiración**: ElevenLabs (cards cálidas) + Vercel (precisión técnica) + Jeton (acento como personalidad)
> **Stack**: CSS Custom Properties + Alpine.js + Bootstrap Icons
> **Perfil**: Lite — 100% frontend estático, sin CDN, sin imports, sin fetch

---

## 1. Filosofía de diseño

**Pergamino digital.** Fondo cálido `#EAF4F5` como canvas principal. 
Las secciones respiran con whitespace generoso. La información se organiza en cards de `#FFFFFF` con bordes sutiles.

**Lime como voz, no como ruido.** `#CFF434` aparece solo donde importa:
- CTA principal (un botón por sección)
- Hover de cards y links
- Badges de secciones destacadas
- Acentos decorativos mínimos

Máximo 10% del área visual. Cuando aparece, que se note.

**Elevación por contraste, no por sombra.** 
- Canvas: `#EAF4F5` (fondo base)
- Cards: `#FFFFFF` (un paso más claro)
- Bordes: `#d0dbdc` (sutiles, 1px)
- Hover: borde pasa a `#CFF434`

**Tipografía como jerarquía.** 
- Headings: Space Grotesk (cuando esté disponible localmente) o Inter Bold
- Body: Inter (400/500)
- Mono: JetBrains Mono (solo bloques de código)

**Patrón de código hexadecimal.** Textura de fondo sutil con fragmentos de código real del stack (Alpine, Dexie, CryptoJS) en opacidad 2-3%, como firma visual única.

---

## 2. Tokens de color

| Token | Hex | Uso |
|-------|-----|-----|
| `--canvas` | `#EAF4F5` | Fondo de página — cálido, claro, fresco |
| `--surface` | `#FFFFFF` | Cards, tarjetas, secciones destacadas |
| `--surface-hover` | `#f7fbfb` | Hover de cards |
| `--surface-teal` | `#024653` | Badges, tags decorativos |
| `--brand-primary` | `#CFF434` | Acento lime — CTAs, hover, highlights |
| `--brand-primary-hover` | `#dbf65a` | Hover del acento lime |
| `--brand-secondary` | `#07D16E` | Badges de éxito, precios |
| `--txt-primary` | `#171614` | Texto principal (casi negro) |
| `--txt-secondary` | `#5a6a6b` | Texto secundario, body |
| `--txt-muted` | `#8a9a9b` | Texto desactivado, metadata |
| `--txt-on-accent` | `#171614` | Texto sobre fondo lime |
| `--border-subtle` | `#d0dbdc` | Bordes de cards, inputs |
| `--border-hover` | `#CFF434` | Borde en hover de interactivos |
| `--border-accent` | `#CFF434` | Focus rings |
| `--shadow-card` | `0 1px 3px rgba(0,0,0,0.06)` | Sombra mínima en cards |

---

## 3. Tipografía

- **Familia headings:** `'Space Grotesk', 'Inter', system-ui, sans-serif` (peso 600-700)
- **Familia body:** `'Inter', system-ui, -apple-system, sans-serif` (peso 400-500)
- **Familia mono:** `'JetBrains Mono', 'Courier New', monospace` (solo código)
- **Fuente local:** Inter Variable en `assets/fonts/InterVariable.woff2`

### Escala de tamaños

| Clase | Tamaño | Weight | Line-Height | Uso |
|-------|--------|--------|-------------|-----|
| `.display` | clamp(2.2rem, 5vw, 3.5rem) | 700 | 1.05 | Hero heading |
| `.h1` | 2.5rem (40px) | 700 | 1.1 | Section headings |
| `.h2` | 1.75rem (28px) | 600 | 1.2 | Sub-headings |
| `.h3` | 1.25rem (20px) | 600 | 1.3 | Card titles |
| `.body` | 1rem (16px) | 400 | 1.6 | Body default |
| `.body-sm` | 0.875rem (14px) | 400 | 1.5 | Secondary text |
| `.caption` | 0.75rem (12px) | 500 | 1.4 | Eyebrows, metadata |
| `.eyebrow` | 0.75rem, 600 weight, 0.08em letter-spacing, uppercase | | | Etiquetas sección |

---

## 4. Espaciado

| Uso | Valor |
|-----|-------|
| Section padding vertical | `5rem` (80px) en mobile, `8rem` (128px) en desktop |
| Card padding | `1.5rem` (24px) |
| Grid gap (apps, precios) | `1.5rem` (24px) |
| Gap entre heading y contenido | `3rem` (48px) |
| Gap entre elementos inline | `0.75rem` (12px) |

---

## 5. Componentes

### Card base
```css
.card-base {
  background: var(--surface);
  border: 1px solid var(--border-subtle);
  border-radius: 12px;
  transition: border-color 200ms ease, transform 200ms ease;
}
.card-base:hover {
  border-color: var(--border-hover);
  transform: translateY(-2px);
}
```

### Botón primario (lime)
```css
.btn-primary {
  background: var(--brand-primary);
  color: var(--txt-on-accent);
  font-weight: 600;
  padding: 0.75rem 1.5rem;
  border-radius: 999px;
  transition: background 150ms ease, transform 150ms ease;
}
.btn-primary:hover {
  background: var(--brand-primary-hover);
  transform: scale(1.02);
}
```

### Botón outline
```css
.btn-outline {
  border: 1px solid var(--border-subtle);
  color: var(--txt-primary);
  padding: 0.75rem 1.5rem;
  border-radius: 999px;
  transition: border-color 200ms ease, color 200ms ease;
}
.btn-outline:hover {
  border-color: var(--brand-primary);
  color: var(--brand-primary);
}
```

### Nav
```css
.nav-glass {
  background: rgba(234, 244, 245, 0.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid var(--border-subtle);
}
```
Estado inicial: transparente. Al scrollear > 50px: nav-glass.

### Badge / Tag
```css
.badge {
  display: inline-flex;
  padding: 0.25rem 0.75rem;
  background: var(--surface-teal);
  color: #EAF4F5;
  border-radius: 999px;
  font-size: 0.75rem;
  font-weight: 500;
}
```

### Precio card
```css
.price-card {
  background: var(--surface);
  border: 1px solid var(--border-subtle);
  border-radius: 16px;
  padding: 2rem;
}
.price-card.featured {
  border-color: var(--brand-primary);
  box-shadow: 0 0 0 1px var(--brand-primary);
}
```

---

## 6. Layout

| Breakpoint | Columnas | Contenedor |
|-----------|----------|------------|
| Mobile < 768px | 1 columna | padding 1.5rem |
| Tablet 768-1024px | 2 columnas | max-width 48rem |
| Desktop > 1024px | 3 columnas (grid) | max-width 72rem |

- Hero: contenido centrado, max-width 48rem
- Nav: full-width, contenido max-width 72rem
- Secciones: padding vertical simétrico

---

## 7. Estrategia de imágenes

- **Sin imágenes externas.** Todo el contenido visual es SVG inline o CSS puro
- **Patrón de código**: generado con CSS pseudo-elementos sobre un grid de líneas, NO una imagen
- **Mockups de apps**: ilustraciones SVG inline estilizadas (sin fotos de stock)
- **Foto de perfil**: única imagen raster, local en `assets/images/`

---

## 8. Estados

| Estado | Implementación |
|--------|---------------|
| Hover | Cards: border-color lime + translateY(-2px). Botones: brighten. Links: color lime |
| Focus | `outline: 2px solid var(--brand-primary); outline-offset: 2px` |
| Active | `transform: scale(0.98)` en botones |
| Scroll reveal | `.reveal` → Intersection Observer → `.visible` → fadeIn + translateY |
| prefers-reduced-motion | Desactivar todas las animaciones. scroll-behavior: auto |

---

## 9. Animaciones

| Elemento | CSS |
|----------|-----|
| Reveal sections | `.reveal { opacity:0; transform:translateY(30px); transition: 0.6s cubic-bezier(0.16,1,0.3,1); } .reveal.visible { opacity:1; transform:translateY(0); }` |
| Hero fade-in | Delays progresivos: `.delay-1` (100ms) a `.delay-5` (500ms) |
| Stagger cards | `transition-delay: calc(var(--i) * 100ms)` |
| FAQ slide | Alpine.js `x-transition:enter="transition ease-out duration-300"` |

---

## 10. Reglas de compliance

1. ✅ Sin CDNs — cada recurso vive en `assets/`
2. ✅ Sin ES6 imports — Alpine.js en script tag
3. ✅ Sin fetch() — contenido estático
4. ✅ Rutas relativas — `./assets/...`
5. ✅ Español primario — toggle EN como secundario
6. ✅ GPU-safe — solo `transform` + `opacity`
7. ✅ Touch targets ≥ 44px
8. ✅ WCAG AA — contraste ≥ 4.5:1
9. ✅ min-h-[100dvh] — no h-screen
10. ✅ prefers-reduced-motion
