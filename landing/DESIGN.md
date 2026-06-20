# DESIGN.md — AHAguilera Landing Page v2

> **Fecha**: 2026-06-19
> **Inspiración**: Craft.do (calidez artesanal) + Linear (precisión técnica) + Raycast (neón sobre oscuro) + SuperHi (código vivo como decoración)
> **Stack**: CSS Custom Properties + Alpine.js 3.15.12 + Bootstrap Icons + Inter Variable local
> **Perfil**: Lite — 100% frontend estático, sin CDN, sin imports, sin fetch, sin type="module"

---

## 1. Filosofía de diseño

**Dual-mode: Cálido ↔ Tech.** La página alterna entre dos mundos visuales:

- **Secciones beige** (`#F5F0EB`): calidez artesanal, confianza, humano. Donde cuento quién soy, qué hago, cómo funciona.
- **Secciones oscuras** (`#171614`): tecnología, potencia, futuro. Donde muestro las apps, los precios, el stack, la comparativa.

La transición entre modos es orgánica — un degradado sutil suaviza el cambio.

**Lime como voz, no como ruido.** `#CFF434` es el acento único y protagonista:
- Brilla sobre fondo oscuro (CTAs, headings, badges, hover)
- Acompaña sobre fondo beige (solo CTAs y hover, con moderación)
- Máximo 10% del área visual. Cuando aparece, que se note.

**Código vivo.** El patrón hexadecimal del fondo no es estático — cambia lentamente como si alguien estuviera escribiendo. Es la firma visual: "esto está hecho de código, y el código está vivo".

**Una app, dos formatos.** Cada aplicación que ofrezco se entrega como:
- 🖥️ `.exe` para Windows (escritorio)
- 📱 `.apk` para Android (móvil)
Sin mensualidades, sin servidor, sin dependencia externa.

---

## 2. Tokens de color — Dual Mode

### Modo Claro (secciones cálidas: Valor, Cómo funciona, Stack, FAQ, Sobre mí)

| Token | Hex | Uso |
|-------|-----|-----|
| `--canvas` | `#F5F0EB` | Fondo de sección — beige natural |
| `--surface` | `#FFFFFF` | Cards, tarjetas, secciones destacadas |
| `--surface-hover` | `#F0EBE6` | Hover de cards |
| `--surface-teal` | `#024653` | Badges, tags decorativos |
| `--brand-primary` | `#CFF434` | Acento lime — solo CTAs y hover |
| `--brand-primary-hover` | `#dbf65a` | Hover del acento lime |
| `--brand-success` | `#07D16E` | Solo semántico (badges éxito, checks) |
| `--txt-primary` | `#171614` | Texto principal |
| `--txt-secondary` | `#6B6560` | Texto secundario, body |
| `--txt-muted` | `#9CA3AF` | Texto desactivado, metadata |
| `--txt-on-accent` | `#171614` | Texto sobre fondo lime |
| `--border-subtle` | `#E0D6CE` | Bordes de cards, inputs |
| `--border-hover` | `#CFF434` | Borde en hover de interactivos |
| `--border-accent` | `#CFF434` | Focus rings |

### Modo Oscuro (secciones tech: Hero, Apps, Precios, Comparativa, CTA final, Footer)

| Token | Hex | Uso |
|-------|-----|-----|
| `--canvas-dark` | `#171614` | Fondo de sección — carbón profundo |
| `--surface-dark` | `#2A2A2A` | Cards en modo oscuro |
| `--surface-dark-hover` | `#333333` | Hover de cards en oscuro |
| `--brand-primary` | `#CFF434` | Acento lime — CTAs, headings, badges, hover |
| `--brand-primary-hover` | `#dbf65a` | Hover del acento lime |
| `--brand-success` | `#07D16E` | Solo semántico |
| `--txt-primary-dark` | `#EAF4F5` | Texto principal sobre oscuro |
| `--txt-secondary-dark` | `#9CA3AF` | Texto secundario sobre oscuro |
| `--txt-muted-dark` | `#6B7280` | Metadata sobre oscuro |
| `--txt-on-accent` | `#171614` | Texto sobre fondo lime |
| `--border-subtle-dark` | `rgba(255,255,255,0.08)` | Bordes en modo oscuro |
| `--border-hover-dark` | `rgba(207,244,52,0.3)` | Borde hover en oscuro |
| `--shadow-card-dark` | `0 1px 3px rgba(0,0,0,0.3)` | Sombra en cards oscuras |

### Gradiente de transición entre modos

```css
.seccion-transicion {
  background: linear-gradient(
    180deg,
    #171614 0%,
    #171614 85%,
    #1A1816 92%,
    #D4CCC2 97%,
    #F5F0EB 100%
  );
}
```

---

## 3. Tipografía

- **Familia:** `'Inter', system-ui, sans-serif` (todo — no hay Space Grotesk disponible localmente)
- **Familia mono:** `'Courier New', 'Consolas', monospace` (solo código hexadecimal decorativo)
- **Fuente local:** Inter Variable en `assets/fonts/InterVariable.woff2`

### Escala de tamaños

| Clase | Desktop | Mobile | Weight | Uso |
|-------|---------|--------|--------|-----|
| `.display` | 4.5rem (72px) | 2.5rem (40px) | 700 | Hero heading |
| `.h1` | 3rem (48px) | 1.75rem (28px) | 700 | Section headings |
| `.h2` | 1.75rem (28px) | 1.25rem (20px) | 600 | Sub-headings |
| `.h3` | 1.25rem (20px) | 1.125rem (18px) | 600 | Card titles |
| `.body` | 1.125rem (18px) | 1rem (16px) | 400 | Body default |
| `.body-sm` | 0.875rem (14px) | 0.875rem | 400 | Secondary text |
| `.caption` | 0.75rem (12px) | 0.75rem | 500 | Eyebrows, metadata |
| `.eyebrow` | 0.75rem, 600, 0.08em letter-spacing, uppercase | | | Etiquetas sección |
| `.codigo` | 0.75rem | 0.65rem | 400 | Hex code decorativo |

---

## 4. Espaciado

| Uso | Valor |
|-----|-------|
| Section padding vertical | `5rem` (80px) mobile, `8rem` (128px) desktop |
| Section padding entre beige↔oscuro | `0` (transición directa con gradiente) |
| Card padding | `1.5rem` (24px) |
| Grid gap (apps, precios) | `1.5rem` (24px) |
| Gap entre heading y contenido | `3rem` (48px) |
| Gap entre elementos inline | `0.75rem` (12px) |
| Hero padding-top | `6rem` (96px) mobile, `8rem` (128px) desktop |

---

## 5. Componentes

### Nav Glass (dinámico)

```css
.nav-glass {
  position: fixed;
  top: 0; left: 0; right: 0;
  z-index: 50;
  transition: background 300ms ease, border-color 300ms ease;
}
.nav-glass.hero-mode {
  background: rgba(23,22,20,0.85);
  backdrop-filter: blur(12px);
  border-bottom: 1px solid rgba(207,244,52,0.1);
}
.nav-glass.light-mode {
  background: rgba(245,240,235,0.88);
  border-bottom: 1px solid rgba(2,70,83,0.12);
}
```

### Logo en nav
- Logo wordmark en lime `#CFF434` sobre hero (oscuro)
- Logo wordmark en `#171614` sobre secciones beige
- Cambia dinámicamente con clase `.light-mode`

### Card base (oscuro)

```css
.card-dark {
  background: var(--surface-dark);
  border: 1px solid var(--border-subtle-dark);
  border-radius: 12px;
  padding: 1.5rem;
  transition: border-color 200ms ease, transform 200ms ease,
              box-shadow 200ms ease;
}
.card-dark:hover {
  border-color: var(--border-hover-dark);
  transform: translateY(-4px);
  box-shadow: 0 8px 30px rgba(207,244,52,0.08);
}
```

### Card base (beige)

```css
.card-light {
  background: var(--surface);
  border: 1px solid var(--border-subtle);
  border-radius: 12px;
  padding: 1.5rem;
  transition: border-color 200ms ease, transform 200ms ease;
}
.card-light:hover {
  border-color: var(--border-hover);
  transform: translateY(-2px);
}
```

### Botón primario (lime — universal)

```css
.btn-primary {
  background: var(--brand-primary);
  color: var(--txt-on-accent);
  font-weight: 700;
  padding: 0.75rem 2rem;
  border-radius: 999px;
  font-size: 1rem;
  transition: background 150ms ease, transform 150ms ease,
              box-shadow 300ms ease;
  cursor: pointer;
}
.btn-primary:hover {
  background: var(--brand-primary-hover);
  transform: scale(1.03);
}
```

### Botón outline (varía por modo)

```css
.btn-outline-dark {
  border: 1px solid rgba(207,244,52,0.3);
  color: var(--brand-primary);
  padding: 0.75rem 2rem;
  border-radius: 999px;
  font-weight: 600;
  transition: border-color 200ms ease, background 200ms ease;
}
.btn-outline-dark:hover {
  border-color: var(--brand-primary);
  background: rgba(207,244,52,0.08);
}

.btn-outline-light {
  border: 1px solid var(--border-subtle);
  color: var(--txt-primary);
  padding: 0.75rem 2rem;
  border-radius: 999px;
  font-weight: 600;
  transition: border-color 200ms ease, color 200ms ease;
}
.btn-outline-light:hover {
  border-color: var(--brand-primary);
  color: var(--brand-primary);
}
```

### App card (oscuro)

```
┌──────────────────────────┐
│  ┌────────────────────┐  │
│  │  SVG mockup app    │  │  ← interfaz simplificada (grids, tabs)
│  └────────────────────┘  │
│                          │
│  Inventario Pro          │  ← h3
│  Control de stock        │  ← body secundario
│  offline-first           │
│                          │
│  🖥️+📱  .exe · .apk    │  ← badge formatos
│  ████████░░░░ 70%       │  ← barra progreso (lime fill)
│  [Ver más →]            │  ← link lime
└──────────────────────────┘
```

### Price card (oscuro — 3 columnas)

| Propiedad | Lite | Standard ⭐ | Custom |
|-----------|------|-----------|--------|
| Background | `var(--surface-dark)` | `var(--surface-dark)` | `var(--surface-dark)` |
| Border | `var(--border-subtle-dark)` | `rgba(207,244,52,0.3)` | `var(--border-subtle-dark)` |
| Box-shadow | none | `0 0 30px rgba(207,244,52,0.08)` | none |
| Badge | none | `"Popular"` lime bg | `"A medida"` teal bg |
| Botón | outline teal | primary lime | outline lime |
| Scale | 1 | 1.05 | 1 |

### Stack card (beige — con flip)

```css
.stack-card {
  perspective: 600px;
  width: 120px;
  height: 120px;
  cursor: pointer;
}
.stack-inner {
  position: relative;
  width: 100%;
  height: 100%;
  transition: transform 0.4s ease-out;
  transform-style: preserve-3d;
}
.stack-card:hover .stack-inner {
  transform: rotateY(180deg);
}
.stack-front, .stack-back {
  position: absolute;
  inset: 0;
  backface-visibility: hidden;
  border-radius: 12px;
  display: flex;
  align-items: center;
  justify-content: center;
}
.stack-front {
  background: var(--surface);
  border: 1px solid var(--border-subtle);
  flex-direction: column;
  gap: 0.5rem;
}
.stack-back {
  background: var(--surface-dark);
  border: 1px solid var(--border-hover-dark);
  transform: rotateY(180deg);
  font-family: 'Courier New', monospace;
  font-size: 0.65rem;
  color: var(--brand-primary);
  padding: 0.75rem;
  text-align: left;
  word-break: break-all;
}
```

### Tabla comparativa (oscuro)

```css
.tabla-comp {
  width: 100%;
  border-collapse: separate;
  border-spacing: 0 8px;
}
.tabla-comp th {
  color: var(--txt-secondary-dark);
  font-weight: 600;
  font-size: 0.875rem;
  text-transform: uppercase;
  letter-spacing: 0.05em;
  padding: 1rem;
  text-align: left;
}
.tabla-comp td {
  padding: 1rem;
  background: rgba(255,255,255,0.03);
  border-radius: 8px;
  color: var(--txt-primary-dark);
}
.tabla-comp .check {
  color: var(--brand-primary);
}
.tabla-comp .cross {
  color: var(--txt-muted-dark);
}
```

### Badge / Tag

```css
.badge-lime {
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  padding: 0.25rem 0.75rem;
  background: var(--brand-primary);
  color: var(--txt-on-accent);
  border-radius: 999px;
  font-size: 0.75rem;
  font-weight: 600;
}
.badge-teal {
  display: inline-flex;
  align-items: center;
  gap: 0.25rem;
  padding: 0.25rem 0.75rem;
  background: var(--surface-teal);
  color: #EAF4F5;
  border-radius: 999px;
  font-size: 0.75rem;
  font-weight: 600;
}
.badge-formato {
  display: inline-flex;
  align-items: center;
  gap: 0.35rem;
  padding: 0.2rem 0.6rem;
  border: 1px solid var(--border-hover-dark);
  color: var(--brand-primary);
  border-radius: 6px;
  font-size: 0.7rem;
  font-weight: 600;
}
```

### CTA Final (oscuro — con pulse)

```css
.btn-cta-final {
  background: var(--brand-primary);
  color: var(--txt-on-accent);
  font-weight: 700;
  padding: 1rem 2.5rem;
  border-radius: 999px;
  font-size: 1.125rem;
  animation: pulse-cta 4s ease-in-out infinite;
}
@keyframes pulse-cta {
  0%, 100% { box-shadow: 0 0 0 0 rgba(207,244,52,0.4); }
  50% { box-shadow: 0 0 0 12px rgba(207,244,52,0); }
}
```

---

## 6. Layout de secciones

### Orden y modo de cada sección

```
 1. HERO         → OSCURO   #171614
 2. VALOR        → BEIGE    #F5F0EB
 3. APPS         → OSCURO   #171614
 4. PRECIOS      → OSCURO   #171614
 5. CÓMO FUNCIONA → BEIGE   #F5F0EB
 6. STACK        → BEIGE    #F5F0EB
 7. COMPARATIVA  → OSCURO   #171614
 8. FAQ          → BEIGE    #F5F0EB
 9. SOBRE MÍ     → BEIGE    #F5F0EB
10. CTA FINAL    → OSCURO   #171614
    FOOTER       → OSCURO   #171614
```

### Hero layout (oscuro)

```
┌──────────────────────────────────────────────┐
│  [Logo lime]  [Nav links]            [🌐 EN] │  glass
│                                                │
│      < línea código hex animado >              │
│      < línea código hex animado >              │
│                                                │
│         APPS OFFLINE-FIRST                     │  display (lime)
│         QUE PARECEN MAGIA                      │  display
│                                                │
│   Tu app. En tu escritorio. En tu bolsillo.    │  body-lg
│   Un desarrollo. Dos formatos:                 │
│   🖥️ .exe + 📱 .apk                           │
│                                                │
│   [Crear mi app →]  [Ver catálogo]             │  btns
│                                                │
│   ──────── ✦ ────────                         │
│   12+ clientes · 8 apps · 4+ años              │  stats
└──────────────────────────────────────────────┘
```

### Valor layout (beige — 2 columnas)

```
┌──────────────────────────────────────────────┐
│  CÓMO FUNCIONA EL SOFTWARE NORMAL             │
│  ┌───┐  ┌───┐  ┌───┐  ┌───┐                 │
│  │ ❌ │  │ ❌ │  │ ❌ │  │ ❌ │                 │
│  │Men-│  │De- │  │Tu  │  │Pa- │                 │
│  │sua-│  │pen-│  │data│  │gas │                 │
│  │li- │  │des │  │en  │  │por │                 │
│  │dad │  │de  │  │la  │  │usua│                 │
│  │    │  │in- │  │nube│  │rio │                 │
│  │    │  │ter-│  │de  │  │    │                 │
│  │    │  │net │  │otro│  │    │                 │
│  └───┘  └───┘  └───┘  └───┘                 │
│                                                │
│  CÓMO TRABAJO YO                               │
│  ┌───┐  ┌───┐  ┌───┐  ┌───┐                 │
│  │ ✅ │  │ ✅ │  │ ✅ │  │ ✅ │                 │
│  │Pa- │  │Ce- │  │Da- │  │.exe│                 │
│  │go  │  │rro │  │tos │  │+   │                 │
│  │una │  │in- │  │ci- │  │.apk│                 │
│  │vez │  │ter-│  │fra-│  │    │                 │
│  │    │  │net │  │dos │  │    │                 │
│  │    │  │    │  │    │  │    │                 │
│  └───┘  └───┘  └───┘  └───┘                 │
│                                                │
│  [Crear mi app →]                              │
└──────────────────────────────────────────────┘
```

---

## 7. Micro-interactividad y animaciones

Todas GPU-safe (solo `transform`, `opacity`, `filter`), todas respetan `prefers-reduced-motion`.

| Elemento | Animación | Duración | Trigger |
|----------|-----------|----------|---------|
| Código hex hero | Un carácter cambia cada 3s con fade 400ms | ∞ | Auto (Alpine setInterval) |
| Nav glass | Fade in/out + cambio de color | 300ms | Scroll > 80px, luego IntersectionObserver con secciones beige |
| Cards app/precio | translateY(-4px) + box-shadow glow | 200ms ease-out | Hover |
| Card Standard precios | scale(1.05) persistente en desktop | — | CSS siempre |
| Stats | Contador 0→N con ease-out | 800ms | IntersectionObserver |
| Stack cards | rotateY(180deg) 3D flip | 400ms ease-out | Hover |
| Scroll reveal | fadeIn + translateY(20px→0) | 600ms | IntersectionObserver |
| Stagger grid | delay escalonado: 0, 100, 200ms | — | Por índice CSS var(--i) |
| FAQ | x-show con fade + slide | 300ms | Click |
| CTA final pulse | box-shadow 0→12px→0 | 4s loop | ∞ (auto) |
| Hero fade-in | opacity 0→1 con delays | 500ms | Page load |

---

## 8. Narrativa de venta (microcopy)

### Hero
> **ES:** Apps offline-first que parecen magia. Pero son código. Tu app. En tu escritorio. En tu bolsillo. Sin internet.
> **EN:** Offline-first apps that look like magic. But they're code. Your app. On your desktop. In your pocket. No internet required.

### Valor — puntos de dolor vs solución
> **❌ Software normal:** Pagas mensualidad · Dependes de internet · Tus datos en la nube de otro · Pagas por usuario
> **✅ Conmigo:** Pagas una vez · Cero internet necesario · Datos cifrados, solo tuyos · .exe + .apk incluidos

### CTA variants
| Sección | Texto |
|---------|-------|
| Hero | Crear mi app → |
| Apps | Ver más → |
| Precios (Lite) | Elegir Lite |
| Precios (Standard) | Elegir Standard → |
| Precios (Custom) | Cotizar → |
| CTA final | Quiero mi .exe + .apk → |
| Footer | angel@ahaguilera.dev |

### Voz de marca
- Primera persona: "Yo construyo", "Trabajo con"
- Sin "nosotros" — eres Ángel
- Sin gerundios pomposos
- Sin falsa urgencia
- El código se menciona con orgullo, no con disculpas

---

## 9. Estrategia de assets

- **Sin imágenes externas.** Todo SVG inline o CSS puro
- **Mockups de apps**: SVG inline con grids, tabs, valores simulados — sin fotos
- **Código hexadecimal**: spans que Alpine.js muta periódicamente
- **Íconos**: Bootstrap Icons (ya en assets/)
- **Logos**: 3 SVGs existentes en `assets/logo/`
- **Foto de perfil**: raster en `assets/images/` (única excepción)

---

## 10. Estados

| Estado | Implementación |
|--------|---------------|
| Hover | Cards: border lime + translateY. Botones: brighten + scale. Links: color lime |
| Focus | `outline: 2px solid var(--brand-primary); outline-offset: 2px` |
| Active | `transform: scale(0.98)` en botones |
| Scroll reveal | `.reveal` → IntersectionObserver → `.visible` → fadeIn + translateY |
| prefers-reduced-motion | Todas las animaciones desactivadas. scroll-behavior: auto |

---

## 11. Reglas de compliance

1. ✅ Sin CDNs — cada recurso vive en `assets/`
2. ✅ Sin ES6 imports — Alpine.js en script tag
3. ✅ Sin fetch() — contenido estático
4. ✅ Sin type="module"
5. ✅ Rutas relativas — `./assets/...`
6. ✅ Español primario — toggle EN con Alpine
7. ✅ GPU-safe — solo `transform` + `opacity`
8. ✅ Touch targets ≥ 44px
9. ✅ WCAG AA — contraste ≥ 4.5:1
10. ✅ min-h-[100dvh] — no h-screen
11. ✅ prefers-reduced-motion
12. ✅ Sin mensualidades, sin servidor — narrativa .exe + .apk
