# Design Spec: Landing Page AHAguilera

> **Fecha**: 2026-06-16
> **Estado**: Aprobado
> **Objetivo**: Landing page completa para vender apps offline-first, capturar leads y mostrar portafolio

---

## 1. Resumen

Landing page one-page scroll con 14 secciones, bilingüe (ES/EN), efectos de scroll, video hero, y diseño dark+light alternado. Stack: HTML + Tailwind CSS local + Alpine.js. Deploy: GitHub Pages.

## 2. Decisiones clave

| Decisión | Elección |
|----------|----------|
| Arquitectura | One-page scroll (1 archivo `index.html`) |
| Objetivo | Vender apps mock + capturar leads + portafolio |
| Apps | 4 apps mock variadas (productividad, finanzas, inventario, salud) |
| Hosting | GitHub Pages |
| Secciones | 14 (hero + 12 contenido + footer) |
| Tono visual | Dark hero + alternas claro/oscuro |
| Contacto | WhatsApp primario + email alternativo |
| Precios | 3 planes fijos + escalamiento por complejidad |
| Idioma | Bilingüe toggle ES/EN (Alpine.js) |
| Stack landing | HTML + Tailwind CSS local + Alpine.js |
| Animaciones | Scroll effects (parallax, sticky, progress bars, fade-in) |
| Hero | Video de fondo (clip código/terminal, loop, sin audio) |

## 3. Estructura de secciones

### 3.1 NAV (sticky)
- Logo wordmark a la izquierda
- Links: Inicio, Apps, Stack, Precios, Sobre mí
- Toggle idioma ES/EN (Alpine.js)
- Backdrop blur, border-bottom sutil
- Highlight del section activo al scroll (Intersection Observer)

### 3.2 HERO (dark, `#171614`)
- Video de fondo: clip de código/terminal en loop, opacidad 30-40%, sin audio
- Logo AHAguilera completo centrado
- Headline: "Apps que funcionan sin internet. Sin servidores. Sin complicaciones."
- Subheadline: "Desarrollo freelance de apps offline-first con stack Alpine + Dexie + Tailwind."
- 2 CTAs: "Empezar ahora" (WhatsApp, primario `#CFF434`) + "Ver apps" (scroll, secundario outline)
- Scroll indicator animado (flecha hacia abajo)
- Animaciones: fade-in delay progresivo (logo → headline → subheadline → CTAs)

### 3.3 PROBLEMA (light, `#EAF4F5`)
- Kicker: "¿POR QUÉ OFFLINE-FIRST?"
- Headline: "El 60% de las apps fallan cuando no hay internet. Las tuyas no deberían."
- 3 pain points en grid:
  1. Icono globe → "Dependes del cloud"
  2. Icono dollar → "Pagas servers cada mes"
  3. Icono lock → "Tus datos no son tuyos"
- Cards con fondo `#ffffff`, borde `#2a2824`

### 3.4 SOLUCIÓN (dark, `#171614`)
- Kicker: "LA SOLUCIÓN"
- Headline: "AHAguilera"
- Grid 2x3 de beneficios con check icons:
  - ✅ Sin servidores
  - ✅ Sin builds
  - ✅ Sin CDNs
  - ✅ Privacidad total
  - ✅ Abrir con doble clic
  - ✅ Deploy = copiar archivos
- Quote: "La mejor infraestructura es la que no existe."
- Background sutil gradient `#171614` → `#1f1d1a`

### 3.5 APPS (light, `#EAF4F5`)
- Kicker: "APPS OFFLINE-FIRST"
- Headline: "Aplicaciones reales que funcionan sin internet"
- Grid 2x2 de apps mock:
  1. **TaskFlow** — Gestor de tareas offline (productividad)
  2. **FinanzaLocal** — Presupuesto familiar (finanzas)
  3. **InventarioPRO** — Control de inventario (negocio)
  4. **SaludTracker** — Registro de salud personal (salud)
- Cada card: screenshot mock (placeholder), nombre, descripción corta, badge de categoría, botón "Ver más"
- Hover: elevación + borde `#CFF434`
- Click: modal con detalles + precio + features

### 3.6 CÓMO FUNCIONA (dark, `#171614`)
- Kicker: "CÓMO FUNCIONA"
- Headline: "3 pasos para tu app"
- Stepper visual horizontal con líneas conectoras:
  1. "Cuéntame tu idea" — "Hablamos de qué necesitas"
  2. "Desarrollo la app" — "La creo con tu stack"
  3. "Descargas y usas" — "La abres con doble clic"
- Números en `#CFF434`, líneas en `#2a2824`
- Scroll animation: cada paso fade-in secuencial

### 3.7 STACK TÉCNICO (light, `#EAF4F5`)
- Kicker: "STACK TÉCNICO"
- Headline: "Tecnologías que no dependen de nadie"
- Logo grid (SVG inline): Alpine.js, Dexie.js, CryptoJS, Tailwind CSS, DaisyUI, Bootstrap Icons
- Tagline: "Cada librería se descarga una vez. El runtime no pide nada a nadie."
- Progress bars animadas (scroll-triggered) mostrando "confiabilidad" de cada tech (100% local)

### 3.8 PRECIOS (dark, `#171614`)
- Kicker: "PRECIOS"
- Headline: "Inversión clara, sin sorpresas"
- 3 cards de precio:
  1. **Lite** ($49) — App básica, 1 módulo, sin crypto
  2. **Standard** ($99, ⭐ POPULAR) — App completa, 3 módulos, crypto, PDF
  3. **Custom** ($199+) — App compleja, módulos ilimitados, todo incluido
- Badge "POPULAR" en Standard con `#CFF434`
- Nota al pie: "* Precios base. Complejidad adicional = precio proporcional."
- CTA en cada card

### 3.9 COMPARATIVA (light, `#EAF4F5`)
- Kicker: "OFFLINE-FIRST vs TRADICIONAL"
- Headline: "Por qué elegir offline-first"
- Tabla comparativa visual:
  - Internet: No req. vs Siempre
  - Costo/mes: $0 vs $20-500
  - Velocidad: Instantánea vs Depende de red
  - Privacidad: 100% local vs En sus servidores
  - Deploy: Copiar vs CI/CD + server
  - Uptime: 100% vs 99.9% (o menos)
- Fila "Offline" con fondo sutil `#024653` opacity 10%
- Scroll animation: filas aparecen una por una

### 3.10 PORTAFOLIO (dark, `#171614`)
- Kicker: "CÓDIGO REAL"
- Headline: "Así se ve tu app por dentro"
- Code snippet real de tu stack (cifrado con CryptoJS + Dexie):
  ```javascript
  const registro = {
    nombre: cryptoHelpers.encrypt(nombre),
    email: cryptoHelpers.encrypt(email),
    createdAt: new Date()
  };
  await db.usuarios.put(registro);
  ```
- Syntax highlighting manual con colores de marca
- Tagline: "Limpio, seguro, sin dependencias externas."

### 3.11 TESTIMONIOS (light, `#EAF4F5`)
- Kicker: "LO QUE DICEN MIS CLIENTES"
- Headline: "Historias reales"
- 3 testimonios mock:
  1. María G., México — "Mi app de inventario funciona sin internet en la bodega."
  2. Carlos R., Colombia — "Por fin un desarrollador que entiende que no todos tienen internet estable."
  3. Ana L., Argentina — "La app de presupuesto familiar cambió cómo organizamos nuestras finanzas."
- Cards con quote marks decorativos `#CFF434`
- Fade-in al scroll

### 3.12 FAQ (dark, `#171614`)
- Kicker: "PREGUNTAS FRECUENTES"
- Acordeón con Alpine.js x-show:
  1. ¿Necesito internet para usar la app?
  2. ¿Mis datos están seguros?
  3. ¿Puedo personalizar la app?
  4. ¿Qué pasa si quiero agregar funcionalidades?
  5. ¿Funciona en celular?
  6. ¿Cuánto tarda en estar lista?
- Animación slide-down suave
- Icono `+` / `×` para abrir/cerrar

### 3.13 SOBRE TI (light, `#EAF4F5`)
- Kicker: "SOBRE MÍ"
- Headline: "Angel Hernández Aguilera"
- Foto placeholder (círculo, borde accent)
- Subtítulo: "Desarrollador Freelance"
- Quote: "Libertad tecnológica. Calidad freelance. Simplicidad radical."
- Skill badges: Alpine.js, Dexie.js, Tailwind CSS, CryptoJS, DaisyUI
- Link a GitHub

### 3.14 CTA FINAL (dark, `#171614`)
- Headline: "¿LISTO PARA EMPEZAR?"
- Subheadline: "Cuéntame tu idea y te digo cómo hacerla realidad offline-first."
- 2 CTAs grandes:
  - WhatsApp: "💬 WhatsApp" (primario `#CFF434`, link a wa.me/521XXXXXXXXXX)
  - Email: "📧 Email" (secundario outline, mailto:angel@ahaguilera.dev)
- Background gradiente sutil `#171614` → `#024653`

### 3.15 FOOTER (dark, `#171614`)
- Logo wordmark centrado
- Links: Proyectos, Stack, Contacto
- Copyright: "© 2026 AHAguilera · MIT License"
- Tagline: "100% offline · Sin CDN · Abrir con doble clic"
- Palette bar decorativa (5 colores de marca)

## 4. Stack técnico

### 4.1 Dependencias (locales, sin CDN)

| Librería | Archivo | Rol |
|----------|---------|-----|
| Tailwind CSS | `assets/css/tailwind.min.css` | Estilos utility-first |
| DaisyUI 5 | `assets/css/daisyui.min.css` | Componentes UI |
| Alpine.js | `assets/js/libs/alpine.js` | Reactividad (toggle, acordeón, smooth scroll) |
| Bootstrap Icons | `assets/css/bootstrap-icons.css` | Iconos SVG |

### 4.2 No se usan (para landing)

| Librería | Razón |
|----------|-------|
| Dexie.js | No hay DB en landing |
| CryptoJS | No hay cifrado en landing |
| ApexCharts | No hay gráficos en landing |
| Animate.css | Scroll effects se hacen con Intersection Observer + CSS |

### 4.3 Estructura de archivos

```
landing/
├── index.html              # Landing completa (1 archivo)
├── assets/
│   ├── css/
│   │   ├── tailwind.min.css
│   │   ├── daisyui.min.css
│   │   └── bootstrap-icons.css
│   ├── js/
│   │   └── libs/
│   │       └── alpine.js
│   ├── video/
│   │   └── hero-bg.mp4     # Clip de código/terminal (loop)
│   └── img/
│       ├── screenshot-taskflow.png
│       ├── screenshot-finanzalocal.png
│       ├── screenshot-inventariopro.png
│       └── screenshot-saludtracker.png
└── brand/
    ├── logo-icon.svg
    ├── logo-wordmark.svg
    └── logo-full.svg
```

## 5. Animaciones y scroll effects

### 5.1 Intersection Observer
- Todas las secciones usan `IntersectionObserver` para detectar cuando entran al viewport
- Clases CSS: `.fade-in`, `.slide-up`, `.slide-left`, `.slide-right`
- Threshold: 0.2 (20% visible para activar)

### 5.2 Efectos específicos
- **Hero**: Parallax sutil en video (translateY al scroll)
- **Nav**: Sticky con backdrop-blur, background-opacidad al scroll
- **Stepper (§5)**: Líneas se dibujan progresivamente
- **Tabla comparativa (§8)**: Filas fade-in secuencial (stagger 100ms)
- **Progress bars (§6)**: Se llenan al 100% al entrar al viewport
- **Cards (§4)**: Hover elevación + borde accent

### 5.3 prefers-reduced-motion
- Si el usuario tiene `prefers-reduced-motion: reduce`, desactivar todas las animaciones
- Video hero se reemplaza por gradiente estático

## 6. Bilingüe (ES/EN)

### 6.1 Implementación
- Alpine.js store `lang` con valor `'es'` o `'en'`
- Cada text tiene `x-show="$store.lang === 'es'"` y `x-show="$store.lang === 'en'"`
- Toggle en nav: botón ES | EN
- Persistencia en `localStorage`

### 6.2 Textos EN (principales)
- Hero: "Apps that work without internet. No servers. No complications."
- Headline: "Offline-first apps built with Alpine + Dexie + Tailwind."
- CTA: "Get started" / "See apps"
- Problema: "Why offline-first?"
- Solución: "The solution: AHAguilera"

## 7. Responsive

### 7.1 Breakpoints
- Mobile: < 768px (1 columna, nav hamburger)
- Tablet: 768px - 1024px (2 columnas donde aplique)
- Desktop: > 1024px (layout completo)

### 7.2 Ajustes mobile
- Nav: hamburger menu con Alpine.js x-show
- Hero: video se reemplaza por gradiente estático
- Grids: 1 columna en mobile
- Stepper: vertical en mobile
- Tabla comparativa: cards apiladas en vez de tabla

## 8. SEO y meta

### 8.1 Meta tags
```html
<title>AHAguilera — Apps Offline-First | Desarrollo Freelance</title>
<meta name="description" content="Desarrollo de apps offline-first sin servidores, sin CDNs. Alpine.js + Dexie + Tailwind. Tus datos, tu control.">
<meta name="keywords" content="offline-first, apps, Alpine.js, Dexie, Tailwind, freelance, desarrollo web">
```

### 8.2 Open Graph
```html
<meta property="og:title" content="AHAguilera — Apps Offline-First">
<meta property="og:description" content="Apps que funcionan sin internet. Sin servidores. Sin complicaciones.">
<meta property="og:type" content="website">
```

## 9. Constraints

- **Sin CDN**: todas las librerías en `assets/`
- **Sin ES6 import/export**: todo con script tags
- **Sin fetch()**: contenido estático
- **Rutas relativas**: siempre `./assets/...`
- **Español primary**: toggle a EN como secundario
- **GPU-safe animations**: solo `transform` + `opacity`
- **Touch targets**: ≥ 44x44px
- **WCAG AA**: contraste ≥ 4.5:1

## 10. Apps mock (contenido)

### TaskFlow
- **Categoría**: Productividad
- **Descripción**: Gestor de tareas offline con etiquetas, prioridades y recordatorios
- **Precio**: Lite ($49)
- **Features**: CRUD tareas, etiquetas, filtro por prioridad, búsqueda local

### FinanzaLocal
- **Categoría**: Finanzas personales
- **Descripción**: Presupuesto familiar con categorías, gráficos y exportación PDF
- **Precio**: Standard ($99)
- **Features**: Ingresos/gastos, gráficos ApexCharts, export PDF con jsPDF, cifrado CryptoJS

### InventarioPRO
- **Categoría**: Negocio
- **Descripción**: Control de inventario con código de barras, stock mínimo y reportes
- **Precio**: Standard ($99)
- **Features**: Productos, stock, alertas stock mínimo, export Excel con SheetJS

### SaludTracker
- **Categoría**: Salud personal
- **Descripción**: Registro de peso, presión, medicamentos y citas médicas
- **Precio**: Lite ($49)
- **Features**: Registro diario, gráficos de tendencia, recordatorios medicación
