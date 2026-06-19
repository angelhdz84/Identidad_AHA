# Filosofía Stack AHAguilera — Identidad de Marca para IA

> **Autor**: Angel Hernández Aguilera— [ahaguilera.dev](https://ahaguilera.dev)
> **Propósito**: Documento de identidad de marca, filosofía técnica y guía de estilo para que cualquier IA replique fielmente el stack, el tono y las decisiones de diseño de AHAguilera.
> **Stack**: Offline-first, Alpine.js, Dexie.js, CryptoJS, Tailwind CSS + DaisyUI, Bootstrap Icons, Animate.css
> **Licencia**: MIT — Uso comercial permitido, atribución recomendada.

---

## 1. Manifiesto — Quién es AHAguilera

AHAguilera no es una agencia ni una empresa. Es un **desarrollador freelance profesional** con una filosofía clara:

> **Libertad tecnológica. Calidad freelance. Simplicidad radical.**

### Valores fundamentales

| Valor | Significado |
|-------|-------------|
| **Offline-first real** | La app funciona sin internet. No hay "modo offline" porque no hay "modo online". Los datos viven en el dispositivo del usuario. |
| **Sin servidores** | No hay backend, no hay API, no hay cloud. Zero DevOps. El deploy es copiar archivos. |
| **Sin builds** | No hay webpack, vite, ni bundler. Abrir `index.html` con doble clic debe funcionar. |
| **Sin CDNs** | Cada librería se descarga una vez en setup y vive en `assets/`. El runtime no pide nada a nadie. |
| **Privacidad por diseño** | Los datos del usuario nunca salen de su dispositivo. El cifrado es obligatorio, no opcional. |
| **Freelance profesional** | Cada entrega es un producto terminado: validado, documentado, empaquetado. |

### Diferenciador clave

Mientras la industria corre hacia más complejidad (microservicios, containers, edge functions, AI ops), AHAguilera corre hacia **menos**. El stack entero cabe en un `index.html` que se abre desde el escritorio.

> _"La mejor infraestructura es la que no existe."_

---

## 2. Stack Tecnológico — El "por qué" de cada elección

### 2.1 Core

| Tecnología | Rol | ¿Por qué esta y no otra? |
|------------|-----|-------------------------|
| **Alpine.js** | Reactividad declarativa en DOM | Sin build step. Sin virtual DOM. Todo en HTML con `x-data`, `x-model`, `x-for`. Funciona en `file://`. |
| **Dexie.js** | Wrapper IndexedDB | API tipo MongoDB sobre IndexedDB nativa. Sintaxis `db.tabla.toArray()`, `bulkAdd()`, índices, versionado de schema. |
| **CryptoJS** | Cifrado AES local | Protege datos sensibles en el dispositivo. Sin servidor, sin TLS. Clave en localStorage. |
| **pako.js** | Compresión ZIP | Exportación de datos comprimidos desde el navegador. Sin servidor. |

### 2.2 UI

| Tecnología | Rol | ¿Por qué? |
|------------|-----|-----------|
| **Tailwind CSS** (local) | Framework CSS utility-first | Sin runtime. Compilado a `.css` estático. `file://` compatible. |
| **DaisyUI 5** | Componentes UI semánticos | Construido sobre Tailwind. Clases como `btn btn-primary`, `card`, `modal`. Accesible por defecto. |
| **Bootstrap Icons** | Set de iconos SVG inline | 1900+ iconos. Funciona sin CDN. Carga como fuente CSS local. |
| **Animate.css** | Animaciones CSS declarativas | Clases como `animate__fadeInUp`. Sin JS. GPU-safe. `file://` compatible. |

### 2.3 Gráficos y utilidades

| Tecnología | Rol |
|------------|-----|
| **ApexCharts** | Gráficos interactivos (barras, líneas, donas, radial) |
| **jsPDF** | Generación de PDF desde el navegador |
| **SheetJS (XLSX)** | Exportación/importación Excel |

### 2.4 Por qué NO

| Tecnología | Motivo del rechazo |
|------------|-------------------|
| React / Vue / Svelte | Requieren build step, bundler, servidor de desarrollo |
| Node.js runtime | La app debe abrirse con doble clic |
| Firebase / Supabase | Dependencia de servidor externo. Violación offline-first |
| GSAP / Framer Motion | Librerías de animación pesadas que requieren CDN |
| Google Fonts CDN | Las fuentes se descargan a `assets/fonts/` en setup |
| TypeScript | Build step requerido. JS vanilla es más compatible con `file://` |

---

## 3. Los Dos Perfiles

### 3.1 Lite (file://)

| Aspecto | Especificación |
|---------|---------------|
| Runtime | Navegador — doble clic en `index.html` |
| DB | Dexie (IndexedDB) |
| Cifrado | CryptoJS con clave en localStorage |
| Módulos JS | ❌ `import`/`export`/`type="module"` (CORS en `file://` bloquea ES6) |
| Build | ❌ Ninguno |
| Librerías | `assets/js/libs/` vía curl en setup |
| PWA | Service Worker opcional |
| Empaquetado | ZIP + GitHub Pages |
| Entrega | Carpeta con `index.html` + `assets/` + `core/` + `modules/` |

### 3.2 Full (Bun --compile .exe)

| Aspecto | Especificación |
|---------|---------------|
| Runtime | Bun `--compile` genera `.exe` nativo |
| DB | Dexie (frontend) + SQLite opcional (backend vía `Bun.sqlite`) |
| Cifrado | CryptoJS (mismo que Lite) |
| Módulos JS | ✅ `import`/`export` permitido en `src/` (Bun bundlea) |
| | ❌ `import` NO permitido en `public/` (código frontend, mismas reglas que Lite) |
| Build | `bun build --compile ./src/index.js --outfile dist/app.exe` |
| Dependencias | `bun add` (npm) |
| Frontend | ~95% idéntico a Lite en `public/` |
| Empaquetado | `.exe` + GitHub Pages + GitHub Release |

### 3.3 Regla de oro

> El frontend Alpine + Dexie + DaisyUI es **~95% idéntico** entre Lite y Full. La diferencia está en el runtime (navegador vs .exe) y el backend (sin servidor vs Bun.sqlite opcional). Una app Lite se migra a Full cambiando solo el entry point y añadiendo `src/server.js`.

---

## 4. Pipeline de Desarrollo

### 4.1 Pipeline Clásico (5 fases)

```
nuevo proyecto
    ↓
iniciar setup → estructura + librerías locales
    ↓
definir spec app → asunciones + preguntas 4+1 + specs/[app].md
    ↓
generar codigo → core/ + modules/ por fases (con pausas)
    ↓
validar app → análisis estático + DevTools + docs/validacion-[app].md
    ↓
publicar → commit + push + Pages + ZIP (Lite) / .exe + Release (Full)
```

### 4.2 Pipeline Supercharged (7 fases)

```
brainstorming → spec → writing-plans → subagents → dual review → deploy
```

Para proyectos complejos con Superpowers instalado. Cada fase tiene checkpoints humanos.

### 4.3 Contratos entre skills

| Skill output | Skill input | Artefacto |
|---|---|---|
| prompt-inicial | setup-init, spec-creator | Nombre + tipo + descripción + perfil |
| setup-init | code-generator | Estructura + librerías según perfil |
| spec-creator | code-generator, design-ux, llm-wiki | `specs/[app].md` v4 |
| design-ux-intelligence | code-generator, ux-refactor | Tono visual + paleta + estilo |
| code-generator | compliance, validation, llm-wiki, ux-refactor, ia-jutia | `modules/*`, `core/*`, `index.html` |
| stack-compliance-guard | code-generator | Validación automática post-generación |
| validation-offline | llm-wiki | `docs/validacion-[app].md` |
| deployment-jigue | — | Commit + push + Pages + ZIP/.exe |
| llm-wiki | — | `wiki/` (páginas markdown) + grafo MCP |

### 4.4 Skills del meta-repo

| Skill | Propósito | Perfiles |
|-------|-----------|----------|
| `prompt-inicial` | Orquestador maestro del pipeline completo | lite, full |
| `setup-init` | Valida entorno, crea estructura, instala librerías | lite, full |
| `spec-creator` | Historia de usuario → spec técnica validada v4 | lite, full |
| `design-ux-intelligence` | Diseño visual + checklist UX crítico | lite, full |
| `stack-compliance-guard` | Guarda automática: bloquea imports, CDNs, fetch, crypto faltante | lite, full |
| `code-generator` | Genera código por fases desde specs, un módulo por turno | lite, full |
| `validation-offline` | Validación estática + DevTools + Playwright E2E + reporte | lite, full |
| `ux-refactor` | Refactor UX/UI 4 fases para apps offline-first existentes | lite, full |
| `ux-ui-universal` | Refactor UX/UI multi-stack vía context7 (React, Django, etc.) | multi-stack |
| `deployment-jigue` | Commit + push + Pages + ZIP (Lite) / .exe + Release (Full) | lite, full |
| `daisyui-patterns` | Patrones DaisyUI 5 + Alpine.js | lite, full |
| `ia-jutia` | Mini IA: FlexSearch (Lite) / +ingesta docs + QA (Full) | lite, full |
| `supercharged-pipeline` | Pipeline potenciado SP+SA | lite, full |
| `llm-wiki` | Wiki persistente (markdown versionado + MCP memory graph) | lite, full |

---

## 5. Reglas No Negociables

Estas reglas son **determinísticas**. Una IA debe verificar cada una antes de generar cualquier output de código.

### 5.1 Stack Compliance (bloqueo automático)

| Categoría | Regla | Sanción |
|-----------|-------|---------|
| **Módulos ES6** | ❌ `import` / `export` / `type="module"` | RECHAZAR. Usar variables globales (`window.`) |
| **CDN en runtime** | ❌ `<script src="http...">` / `<link href="http...">` | RECHAZAR. Usar ruta local `assets/js/libs/` |
| **Fetch/axios** | ❌ `fetch()` / `axios` / `XMLHttpRequest` | RECHAZAR. Usar Dexie (IndexedDB) |
| **Cifrado** | ✅ `cryptoHelpers.encrypt()` en campos sensibles | OBLIGATORIO. Si falta: RECHAZAR |
| **UI** | ✅ DaisyUI + Bootstrap Icons + Animate.css | OBLIGATORIO. Sin excepciones |
| **Variables globales** | ✅ `Alpine`, `Dexie`, `CryptoJS`, `window.db`, `window.UI` | OBLIGATORIO. Compatibilidad `file://` |
| **Rutas** | ✅ Relativas siempre (`assets/js/libs/...`) | OBLIGATORIO. Sin rutas absolutas |
| **Idioma** | ✅ Español en UI, comentarios, docs, variables | OBLIGATORIO |

### 5.2 Anti-patrones de diseño (AI Tells)

Patrones que delatan UI genérica hecha por IA. Detectables con grep:

| # | Patrón prohibido | Corrección |
|---|-----------------|------------|
| 1 | `border-l-4 border-primary` (side-stripe) | Fondo tintado o icono leading |
| 2 | `bg-gradient-to-r from-purple-500 to-blue-500 bg-clip-text text-transparent` (gradient text) | Color sólido |
| 3 | `backdrop-blur-xl bg-white/10` decorativo (glassmorphism) | Solo si cumple propósito funcional |
| 4 | Big number + small label (hero-metric template) | Contenido real, testimonios |
| 5 | Card grids idénticos (icon + heading + text repetido) | Variar layouts, mezclar tipos |
| 6 | Modal como primera opción | Agotar alternativas inline primero |
| 7 | Cards anidadas | Extraer contenido a su sección |
| 8 | `text-gray-500` sobre `bg-primary` | Shade más oscuro del color de fondo |
| 9 | `#000` o `#fff` puro | Tintar hacia hue brand (chroma 0.005-0.01) |
| 10 | Bounce/elastic easing | `ease-out-quart` / `quint` / `expo` |
| 11 | Animación de layout properties | Solo `transform` + `opacity` |
| 12 | Purple-to-blue gradients | Elegir UN color sólido como acento |
| 13 | Inter como única tipográfica | `system-ui` o fuente con personalidad |
| 14 | Rounded-square icon tile arriba de headings | Quitar icon tile o icono inline |
| 15 | Em dashes en copy (`—`) | Coma, dos puntos o paréntesis |
| 16 | Tiny uppercase tracked labels sobre cada sección | Un kicker fuerte basta |
| 17 | Monospace como shorthand "técnico" | Solo si la marca es genuinamente técnica |
| 18 | Dark mode = light mode invertido | Jerarquía propia (surface lighter = depth) |
| 19 | Centered stack hero con icon-card-grid | Asimetría, left-aligned |
| 20 | All-caps body copy | Reservar caps para labels cortos |
| 21 | Placeholder text con bajo contraste | 4.5:1 mínimo también en placeholder |
| 22 | Heavy color en estados inactivos | Inactivo = muted, activo = acento |
| 23 | Nested modales | Steps progresivos en línea |
| 24 | Sin skeleton states en carga | Skeleton > spinner-in-the-middle |
| 25 | Sin empty states que enseñen | Empty state que guía al primer paso |
| 26 | Display fonts en UI labels o botones | Sans para UI, display solo para branding |
| 27 | Sin state coverage (hover/focus/active/disabled) | Cada interactivo tiene sus 5 estados |
| 28 | Acentos saturados >80% | Desaturar a chroma < 0.08 |
| 29 | Nombres genéricos ("Acme Corp", "SmartFlow") | Nombres reales o contextuales |
| 30 | Números falsos (99.99%, $100.00) | Datos orgánicos (47.2%) |
| 31 | Lorem Ipsum / placeholder text | Copy real |
| 32 | Emojis en UI | Bootstrap Icons o SVG |
| 33 | `h-screen` | `min-h-[100dvh]` |
| 34 | Icons sin label contextual | `sr-only` o `aria-label` |

---

## 6. Filosofía de Diseño

### 6.1 Interface Discovery (5 pasos)

Antes de elegir paletas, tipografías o estilos, ejecutar:

1. **Intent Exploration** — ¿Quién usará esto? ¿Qué emoción debe transmitir? (calma, energía, precisión, calidez, prestigio)
2. **Domain Exploration** — ¿Qué colores aparecen naturalmente en este dominio? ¿Cuál es el signature element?
3. **Subtle Layering** — 2-4 niveles de surface elevation. Sin sombras dramáticas. La profundidad se siente, no se anuncia.
4. **Infinite Expression** — Cada pantalla emerge de su tarea. Una lista no se ve igual que un formulario.
5. **Systemic Intent** — Cada decisión refuerza el "feel" declarado. Consistencia > creatividad.

### 6.2 Tonos visuales predefinidos

| # | Tono | Paleta | Cuándo usarlo |
|---|------|--------|---------------|
| 1 | Profesional limpio | Slate/blue, sombras sutiles, sans-serif | Enterprise, B2B, dashboards |
| 2 | Moderno vibrante | Gradientes suaves, acentos teal/purple | Startups, SaaS moderno |
| 3 | Minimalista premium | Whitespace extremo, font-weight variable | Portfolios, landing pages |
| 4 | Editorial/magazine | Layout asimétrico, serif en títulos | Blogs, medios, contenido |
| 5 | Retro-futurista | Bordes asimétricos, neón suave | Gaming, tech experimental |
| 6 | Vercel Precision | Monocromo, shadow-as-border, negative tracking | Developer tools, plataformas |
| 7 | Linear Dark | Canvas #010102, acento lavender #5e6ad2 | Apps oscuras premium |
| 8 | Stripe Indigo | Navy ink #0d253d, índigo CTA #533afd | Fintech, SaaS enterprise |

### 6.3 Paletas por tipo de app

| Tipo | Primario | Secundario | Acento |
|------|----------|------------|--------|
| SaaS General | `#2563EB` | `#3B82F6` | `#EA580C` |
| Micro SaaS | `#6366F1` | `#818CF8` | `#059669` |
| E-commerce | `#059669` | `#10B981` | `#EA580C` |
| Healthcare | `#0891B2` | `#22D3EE` | `#059669` |
| Fintech/Crypto | `#F59E0B` | `#FBBF24` | `#8B5CF6` |
| Developer Tool | `#1E293B` | `#334155` | `#22C55E` |
| AI/Chatbot | `#7C3AED` | `#A78BFA` | `#0891B2` |

### 6.4 Tipografía

Reglas:
- Sistema de 5 tamaños con ratio fijo (1.25 o 1.333)
- Nombres semánticos: `--text-body`, `--text-heading`, nunca `--font-size-16`
- Body mínimo 16px. Máx 64ch por línea.
- `rem` fijo en UI. `clamp()` en displays.
- Una familia basta (pesos variados crean jerarquía).
- Nunca `px` en font-size. Nunca `user-scalable=no`.

Pairings recomendados:

| Contexto | Títulos | Cuerpo |
|----------|---------|--------|
| Corporativo | Poppins | Open Sans |
| Tech startup | Space Grotesk | DM Sans |
| Dashboard | Inter | Inter |
| Developer tool | JetBrains Mono | IBM Plex Sans |
| SaaS moderno | Plus Jakarta Sans | Plus Jakarta Sans |
| Healthcare | Figtree | Noto Sans |
| Fintech | IBM Plex Sans | IBM Plex Sans |

### 6.5 Motion Design

- **Spring physics** en elementos interactivos: `cubic-bezier(0.34, 1.56, 0.64, 1)`
- **Duración**: 150-400ms (100/300/500 rule)
- **GPU-safe**: solo `transform` + `opacity`. Nunca `top`, `left`, `width`, `height`.
- **Stagger**: delay incremental en listas/grids (`i * 80ms`)
- **Skeleton loaders** siempre que haya carga asíncrona (shimmer gradiente animado)
- **Sin decoración por decoración**. Cada animación explica algo: fadeIn = aparece, slide = se mueve, scale = cambia importancia.
- **Respetar** `prefers-reduced-motion`

### 6.6 Accesibilidad (WCAG AA mínimo)

- Contraste texto/fondo ≥ 4.5:1
- Labels visibles en inputs (no solo placeholder)
- `aria-label` en botones con solo icono
- `aria-live="polite"` en regiones dinámicas (toast, alerts)
- `role="alert"` en mensajes de error
- `aria-current="page"` en nav activo
- Focus ring visible: `focus:ring-2 focus:ring-primary focus:ring-offset-2`
- Skip link al inicio
- Touch targets ≥ 44x44px
- Landmark roles: `<header role="banner">`, `<nav role="navigation">`, `<main role="main">`
- Cada pantalla tiene un `<h1>` único

---

## 7. Patrones de Código Obligatorios

### 7.1 Estructura de un módulo

```javascript
const NombreModulo = {
  id: 'id-lowercase',
  titulo: 'Título Visible',
  icono: 'bi bi-icon-name',

  async init() {
    console.log(`💡 [${this.id}] Inicializado`);
  },

  async render(params = {}) {
    return `...`; // HTML con Alpine + DaisyUI
  },

  destroy() {
    // Cleanup
  }
};

window.MODULES = window.MODULES || {};
window.MODULES[NombreModulo.id] = NombreModulo;
```

### 7.2 Orden de carga en index.html

```html
<!-- 1. CSS base -->
<link rel="stylesheet" href="assets/css/tailwind.min.css">
<link rel="stylesheet" href="assets/css/daisyui.min.css">
<link rel="stylesheet" href="assets/css/bootstrap-icons.css">
<link rel="stylesheet" href="assets/css/animate.min.css">
<!-- CSS adicional (si hay) -->

<!-- 2. JS Librerías base -->
<script src="assets/js/libs/alpine.js"></script>
<script src="assets/js/libs/dexie.js"></script>
<script src="assets/js/libs/crypto-js.js"></script>
<script src="assets/js/libs/pako.js"></script>
<script src="assets/js/libs/apexcharts.js"></script>
<script src="assets/js/libs/jspdf.js"></script>
<script src="assets/js/libs/xlsx.js"></script>

<!-- 3. JS Librerías adicionales (desde spec) -->

<!-- 4. Core -->
<script src="core/db.js"></script>
<script src="core/crypto.js"></script>
<script src="core/ui.js"></script>
<script src="core/theme.js"></script>
<script src="core/app.js"></script>

<!-- 5. Main -->
<script src="main.js"></script>
```

### 7.3 Cifrado de campos sensibles

```javascript
const registro = {
  nombre: cryptoHelpers.encrypt(datos.nombre),
  email: cryptoHelpers.encrypt(datos.email),
  telefono: datos.telefono, // No sensible
  createdAt: new Date()
};
await db.tabla.put(registro);
```

### 7.4 Patrón Result Type para operaciones offline

```javascript
const Result = {
  ok(value) { return { success: true, value }; },
  fail(error) { return { success: false, error }; }
};

async function guardarRegistro(tabla, datos, camposSensibles = []) {
  try {
    const registro = { ...datos, updatedAt: new Date() };
    for (const campo of camposSensibles) {
      if (registro[campo]) {
        registro[campo] = cryptoHelpers.encrypt(registro[campo]);
      }
    }
    await db[tabla].put(registro);
    UI.toast('Guardado correctamente', 'success');
    return Result.ok(registro);
  } catch (err) {
    UI.toast('Error al guardar: ' + err.message, 'error');
    return Result.fail(err.message);
  }
}
```

### 7.5 Template HTML de módulo (Alpine + DaisyUI)

```html
<div x-data="idData()" x-init="init()" class="animate__animated animate__fadeInUp">
  <h2 class="text-2xl font-bold mb-4 flex items-center gap-2">
    <i class="bi bi-icon-name"></i> Título
  </h2>
  <div class="card bg-base-100 shadow-xl p-4">
    <label class="form-control w-full">
      <span class="label-text">Nombre</span>
      <input type="text" x-model="form.nombre" class="input input-bordered focus:ring-2 focus:ring-primary" />
    </label>
    <button class="btn btn-primary mt-4" @click="guardar()">
      <i class="bi bi-check-lg"></i> Guardar
    </button>
  </div>
</div>
```

### 7.6 Estados de UI

```html
<!-- Empty state -->
<div class="text-center py-12 animate__animated animate__fadeIn">
  <i class="bi bi-inbox text-6xl text-base-300"></i>
  <h3 class="text-lg font-medium mt-4">Sin registros</h3>
  <p class="text-sm text-base-content/60 mt-1">Agrega tu primer elemento para empezar</p>
  <button class="btn btn-primary mt-4" @click="abrirFormulario()">
    <i class="bi bi-plus-lg"></i> Agregar
  </button>
</div>

<!-- Loading skeleton -->
<div class="space-y-4 animate-pulse">
  <div class="flex items-center gap-4">
    <div class="w-12 h-12 bg-base-300 rounded-full"></div>
    <div class="flex-1 space-y-2">
      <div class="h-4 bg-base-300 rounded w-3/4"></div>
      <div class="h-3 bg-base-300 rounded w-1/2"></div>
    </div>
  </div>
</div>

<!-- Error state -->
<div class="alert alert-error shadow-lg">
  <i class="bi bi-exclamation-triangle"></i>
  <span>No se pudieron cargar los datos</span>
  <button class="btn btn-sm btn-ghost" @click="cargar()">
    <i class="bi bi-arrow-clockwise"></i> Reintentar
  </button>
</div>

<!-- Offline banner -->
<div x-show="!$store.network?.online"
     class="fixed top-0 inset-x-0 bg-warning text-warning-content text-center text-sm py-1 z-50
            animate__animated animate__slideInDown">
  <i class="bi bi-wifi-off"></i> Sin conexión — los datos se guardan localmente
</div>
```

---

## 8. Identidad de Marca AHAguilera

### 8.1 Voice & Tone

| Atributo | Cómo se manifiesta |
|----------|-------------------|
| **Técnico pero accesible** | Explica conceptos sin jargon innecesario. "Dexie guarda en IndexedDB" no "wrapper de object stores con promisificación". |
| **Directo, sin relleno** | Respuestas de menos de 4 líneas cuando sea posible. Sin introducciones ni conclusiones. |
| **En español siempre** | UI, comentarios, documentación, variables, commits. El mercado es hispanohablante. |
| **Freelance profesional** | Cada entrega es un producto terminado, no un prototipo. Validado, documentado, listo para entregar. |
| **Sin emojis en UI** | Los emojis son para documentación interna y comunicación con la IA. En la UI se usan Bootstrap Icons. |

### 8.2 Público objetivo

- Freelancers latinoamericanos que quieren entregar apps funcionales sin depender de infraestructura cloud
- Pequeñas y medianas empresas que necesitan herramientas internas sin pagar servidores
- Desarrolladores que valoran la simplicidad y el control total sobre su stack

### 8.3 Diferenciador de marca

> **AHAguilera no compite con frameworks modernos — compite con la complejidad.**

Mientras el mercado empuja hacia más abstracción (Next.js, server components, edge computing), AHAguilera demuestra que se puede construir software profesional con un `index.html` y librerías descargadas una vez. No es "retroceso" — es **libertad**.

### 8.4 Colores de marca

| Rol | Color | Hex |
|-----|-------|-----|
| Brand primary | Indigo profundo | `#1E293B` |
| Brand accent | Verde técnico | `#22C55E` |
| Brand secondary | Slate claro | `#64748B` |
| Background | Blanco | `#FFFFFF` |
| Texto | Slate 900 | `#0F172A` |

### 8.5 Tipografía de marca

- **Títulos**: Space Grotesk (tech, moderno, distintivo)
- **Cuerpo**: DM Sans (limpia, legible, amigable)
- **Código**: JetBrains Mono (técnico, preciso)

### 8.6 Recursos de marca

- Web: [ahaguilera.dev](https://ahaguilera.dev)
- GitHub: [@angelhdz84](https://github.com/angelhdz84)
- Repo principal: [SKILLS-AHAGUILERA](https://github.com/angelhdz84/SKILLS-AHAGUILERA)
- Licencia: MIT

---

## 9. Guía para la IA — Cómo replicar este stack

### 9.1 Al recibir una petición de código

1. **Leer la spec** en `specs/[app].md` (si existe)
2. **Validar compliance** contra reglas no negociables (sección 5)
3. **Aplicar tono visual** definido en la spec o preguntar si no existe
4. **Generar un módulo a la vez** con pausa entre cada uno
5. **Validar nuevamente** antes de mostrar output
6. **Marcar correcciones** con `🛡️ Ajustado a reglas offline-first`

### 9.2 Estructura de respuesta

```
📦 MÓDULO: [nombre-id]
### `modules/[nombre-id]/module.js`
[código completo]

### `modules/[nombre-id]/module.html`
[código completo]

🛡️ Stack Compliance: ✅ Validado (sin imports, rutas relativas, cifrado aplicado, UI consistente)
⏸️ PAUSA. Responde "✅ [nombre-id] OK" para el siguiente módulo.
```

### 9.3 Comandos slash del ecosistema

| Comando | Trigger | Efecto |
|---------|---------|--------|
| `/new` | `nuevo proyecto` | Pipeline clásico 5 fases |
| `/setup` | `iniciar setup` | Crea estructura + instala librerías |
| `/spec` | `definir spec app` | spec-creator interactivo |
| `/build` | `generar codigo` | Fase A (core) + Fase B (módulos) |
| `/test` | `validar app` | Estático + DevTools + Playwright |
| `/compliance` | — | stack-compliance-guard manual |
| `/status` | — | Lee pipeline state |
| `/archive` | — | Archiva spec + reporte |
| `/deploy` | `publicar` | deployment-jigue |
| `/pro` | `pipeline potenciado` | Pipeline supercharged 7 fases |
| `/ia` | `mini ia` | ia-jutia (Lite/Full/No) |
| `/docs` | — | Abre guia-skills-mcps.html |

### 9.4 Perfiles de IA Jutia

| Perfil | Capacidades |
|--------|------------|
| Lite | FlexSearch + estadísticas + predicciones sobre datos de la app |
| Full | Todo lo anterior + ingesta PDF/DOCX/XLSX/CSV/MD + Transformers.js QA extractivo |
| No | Sin módulo IA |

Acceso: por módulo específico + atajo global Cmd+K.

---

## 10. Checklist de Validación Final

Antes de entregar cualquier output de código, verificar:

```
🛡️ CHECKLIST FINAL — STACK A.HERNANDEZ

[ ] ¿Sin import/export/type="module"?
[ ] ¿Sin CDNs/fetch/axios en runtime?
[ ] ¿Campos sensibles cifrados con cryptoHelpers.encrypt()?
[ ] ¿UI con DaisyUI + Bootstrap Icons + Animate.css?
[ ] ¿Módulo registrable en project.config.js?
[ ] ¿Rutas relativas?
[ ] ¿Orden de scripts correcto (CSS → Libs → Core → Main)?
[ ] ¿Sin anti-patrones de diseño (AI tells)?
[ ] ¿Estado offline visible (banner/badge)?
[ ] ¿Loading states en operaciones async?
[ ] ¿Empty states guían al usuario?
[ ] ¿Focus rings visibles?
[ ] ¿aria-label en icon buttons?
[ ] ¿Mensajes de error en español?
[ ] ¿Touch targets ≥ 44x44px?
[ ] ¿min-h-[100dvh] en lugar de h-screen?
[ ] ¿GPU-safe (solo transform + opacity)?
[ ] ¿prefers-reduced-motion respetado?
```

---

## Apéndice: MCP Servers

| Server | Propósito | Setup |
|--------|-----------|-------|
| `stocky` | Busca imágenes Pexels + Unsplash | `pip install -e ./mcp-servers/stocky/` |
| `refero-styles` | Busca sistemas de diseño en refero.design | `npm install && npm run build` en `mcp-servers/refero-styles/` |

---

> _Documento generado desde el meta-repo SKILLS-AHAGUILERA v2.0_  
> _Cualquier IA puede usar este documento para replicar fielmente el stack, el tono y las decisiones de diseño de AHAguilera._  
> _Consultas, issues y PRs en [github.com/angelhdz84/SKILLS-AHAGUILERA](https://github.com/angelhdz84/SKILLS-AHAGUILERA)_
