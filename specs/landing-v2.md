# spec: landing-v2

## 1. Descripción general

**Landing page profesional** para AHAguilera — desarrollador freelance de apps offline-first.
Un híbrido entre catálogo de productos y presentación de servicios, implementado como Enfoque A (Cálido-Tech) con sistema dual-mode beige/carbón.

- **Audiencia**: Mipymes latinoamericanas, freelancers, emprendedores no técnicos
- **Problema que resuelve**: Dueños de negocio que necesitan apps funcionales sin pagar servidores ni depender de internet
- **Propuesta única**: Apps que se abren con doble clic, funcionan sin internet, y los datos son 100% del usuario

## 2. Stack técnico

| Tecnología | Rol | Archivo |
|-----------|-----|---------|
| CSS Custom Properties | Sistema de diseño dual-mode | En `_head.html` (CSS inline) |
| Alpine.js 3.x | Reactividad (toggle, acordeón, lang, scroll) | `assets/js/libs/alpine.js` |
| Bootstrap Icons | Iconos SVG | `assets/css/bootstrap-icons.css` |
| Inter Variable | Tipografía principal | `assets/fonts/InterVariable.woff2` |

**Prohibiciones** (stack compliance):
- ❌ Sin CDNs, sin `import`/`export`, sin `fetch()`, sin `type="module"`
- ❌ Sin Tailwind/DaisyUI (CSS nativo con custom properties + animaciones CSS)
- ✅ Rutas relativas siempre (`./assets/...`)

## 3. Secciones / Módulos

La landing es de UNA página implementada en 4 parciales que se concatenan. Las secciones son:

| # | Sección | Modo | Componentes clave | Alpine.js |
|---|---------|------|------------------|-----------|
| 1 | Nav flotante | Carbón | Logo circular (logotipo.jpg 2rem), links, toggle ES/EN, hamburguesa móvil | `x-data`, `x-model` lang, `x-show` menú |
| 2 | Hero | Carbón | Headline, punchline, 1 CTA principal, badge .exe+.apk, stats, terminal panel | x-show lang |
| 3 | Valor | Beige | 3 cards con iconos + bloque comparativo "Software normal vs Cómo trabajo yo" | Intersection Observer |
| 4 | Apps | Carbón | Grid catálogo (InventarioPRO, FacturaExpress, ClienteSeguro, GastosDiarios) | Modales `x-show` |
| 5 | IA Jutia | Carbón | Mini IA offline-first, perfiles Lite/Full, bloque comparativo competencia | — |
| 6 | Precios | Carbón | 3 planes (Lite $49, Standard $99⭐, Custom $199+) con IA Jutia incluida | — |
| 7 | Cómo funciona | Beige | 3 pasos + timeline vertical | Intersection Observer |
| 8 | Stack flip | Carbón | 6 cards flip 3D (frontal=tecnología, trasera=beneficio cliente) | — |
| 9 | Comparativa | Carbón | Tabla offline-first vs SaaS tradicional | Stagger animation |
| 10 | FAQ | Beige | 7 preguntas acordeón (incluye "¿Qué es IA Jutia?") | `x-show` + `x-transition` |
| 11 | Sobre mí | Carbón | Bio, skills badges, badge IA Jutia | — |
| 12 | CTA Final | Carbón | WhatsApp + Email con íconos grandes | — |
| 13 | Footer | Beige | Logo circular (logotipo.jpg 2.5rem), links redes, tagline | — |

## 4. Flujos de usuario

### Flujo principal: Visitante → Cliente
1. Llega a la landing
2. Ve hero → entiende propuesta de valor en segundos
3. Scrollea a Apps → ve apps disponibles con precios
4. Si le interesa una app → clic "Comprar / Lo quiero" → WhatsApp directo con texto predefinido
5. Si quiere IA → scrollea a IA Jutia → elige Lite o Full
6. Scrollea Precios → elige plan
7. FAQ resuelve dudas (incluye "¿Qué es IA Jutia?")
8. CTA Final → WhatsApp o Email

### Flujo secundario: Visitante escéptico
1. Llega y duda → scrollea "Valor" bloque comparativo
2. Ve "Cómo funciona" + "Stack flip" (beneficios cliente)
3. Comparativa offline-first vs tradicional
4. Lee "Sobre mí" + badge IA Jutia
5. FAQ resuelve objeciones
6. CTA Final

## 5. Hero redesign (Enfoque A)

| Elemento | Descripción |
|---------|------------|
| **Lime headline** | AHApp en 1.4em con glow (text-shadow:0 0 40px rgba(207,244,52,0.25)) |
| **Punchline** | "Tu app. En .exe + .apk. Sin internet. Sin mensualidades." — reemplaza subheadline + format badge |
| **Single CTA** | "Crear mi app →" (lime pill) + subtle link "Ver catálogo de apps →" |
| **Stats narrative** | "clientes que repiten", "apps entregadas este año", "años sin servidores" |
| **Tagline** | "Apps offline-first que parecen magia." (single line) |
| **Terminal panel** | Right column: border 1px rgba(207,244,52,0.15), bg rgba(207,244,52,0.03), border-radius 12px, fadeIn animado, progress bar "██▓▓▒▒░░░░░░░ 100% offline" |

## 6. Reglas de negocio

- Los precios son fijos y visibles (sin "cotización")
- Los planes Lite/Standard tienen features delimitados; IA Jutia Lite incluida en plan Lite, IA Jutia Full en Standard y Custom
- Custom es elástico: "dime tu idea y te presupuesto"
- Todos los CTAs principales → WhatsApp (primario) o Email (alternativo)
- No hay carrito de compras, no hay checkout online → lead generation vía WhatsApp
- **WhatsApp real**: +5355944628 (Cuba)
- Cada app del catálogo tiene texto predefinido en el enlace WhatsApp (ej: `?text=Quiero%20InventarioPRO`)
- Los 13 CTAs del footer social son solo iconos decorativos (sin enlace)

## 6. Perfil

**Lite** — La landing es 100% frontend estático. Sin base de datos, sin backend. Sin build step. Funciona en `file://`.

## 7. Brand Voice (Cálido-Tech)

| Atributo | Cómo se manifiesta |
|----------|-------------------|
| **Cercano pero profesional** | "Tu app funciona sin internet" no "solución cloud-agnostic offline-capable" |
| **Directo, sin rodeos** | Frases cortas. Sin párrafos de relleno |
| **En español hispano** | "Doble clic y funciona" — no "double click and it works" |
| **Confianza silenciosa** | El código habla. No necesita testimonios falsos ni sellos |
| **Lime como identidad** | El acento `#CFF434` es parte del discurso visual, máximo 10% |
| **Artisanal + Tech** | Secciones beige cálidas alternan con oscuras futuristas |

## 8. Brand Narrative

**Tesis central**: La mejor infraestructura es la que no existe.

**Historia**: AHAguilera nace de una convicción — el software debería liberar, no esclavizar. Mientras la industria corre hacia más complejidad, AHAguilera corre hacia menos. Tus datos en tu máquina. Tu app en tu escritorio. Sin mensualidades, sin servidores, sin que te vendan "la nube" como única opción.

**Tagline**: "Apps que funcionan sin internet. Sin servidores. Sin complicaciones."

**Diferenciador IA Jutia**: Inteligencia artificial que corre 100% local. Sin conexión, sin enviar datos a nadie, sin suscripción.

## 9. Design Principles

1. **Claridad sobre creatividad** — Cada elemento tiene un propósito. Sin decoración vacía.
2. **Menos es más** — Whitespace generoso. Una idea por sección.
3. **El acento lime es voz, no ruido** — Aparece en CTAs, transiciones, highlights. Máximo 10% del área visual.
4. **Micro-interactividad con sentido** — Las animaciones explican (fade-in = aparece, hover = es interactivo). No se anima por animar.
5. **Mobile-first** — Todo funciona en móvil. Touch targets ≥ 44px.
6. **GPU-safe** — Solo propiedades `transform` y `opacity` en animaciones.

## 10. Personas

| Persona | Descripción | Comportamiento |
|---------|------------|----------------|
| **María, Mipyme** | Dueña de tienda física, 45 años, no técnica | Quiere llevar inventario sin pagar internet. Scrollea lento, lee todo. Confía si ve "sin internet" |
| **Carlos, Freelancer** | Contador, 30 años, algo técnico | Busca apps de presupuesto. Compara precios. Valora privacidad. Llega a sección precios directo |
| **Ana, Emprendedora** | 28 años, varios proyectos | Necesita apps rápidas sin compromiso. Valora IA local. Compara perfiles Lite/Full de IA Jutia |

## 11. States

| Estado | Estrategia |
|--------|-----------|
| Loading | No aplica (landing estática pura, sin async data) |
| Hover | Cards: borde lime `#CFF434` o `box-shadow`. CTAs: lime más brillante `#dbf65a`. Nav links: color lime |
| Focus | `outline: 2px solid #CFF434; outline-offset: 2px` |
| Active/Click | Scale sutil `transform: scale(0.98)` |
| Flip card | `transform: perspective(1000px) rotateY(180deg)` con `backface-visibility: hidden` |

## 12. Motion Design

| Elemento | Animación | Timing | Easing |
|----------|-----------|--------|--------|
| Hero headline | fadeIn + translateY(20→0) | 600ms | cubic-bezier(0.16, 1, 0.3, 1) |
| Secciones al scroll | fadeIn + translateY(30→0) | 500ms | ease-out |
| Cards hover | border-color + translateY(-2px) | 200ms | ease-out |
| Flip 3D stack | perspective rotateY(0→180°) | 500ms | ease-in-out |
| FAQ toggle | height + opacity | 300ms | ease-out |
| CTA hover | scale(1.02) + brighter lime | 150ms | ease-out |
| Gradiente de transición | background-color con transition 0.6s | 600ms | ease |
| Transición modo crawl | No hay modo crawl — el modo es por sección (no toggle) |

## 13. Librerías adicionales

Ninguna. Stack mínimo: Alpine.js + Bootstrap Icons + Inter font local. CSS nativo con custom properties + `@keyframes`.

## 14. Archivos de la landing

| Archivo | Rol | Generado |
|---------|-----|----------|
| `_head.html` | CSS + meta tags + OG/Twitter | No — se edita directamente |
| `_body1.html` | Nav + Hero + Valor | No — se edita directamente |
| `_body2.html` | Apps + IA Jutia + Precios + Cómo funciona | No — se edita directamente |
| `_body3.html` | Stack flip + Comparativa + FAQ + Sobre mí + CTA + Footer | No — se edita directamente |
| `index.html` | Landing completa concatenada | Sí — `Get-Content -Encoding UTF8 _head.html,_body1.html,_body2.html,_body3.html \| Set-Content -Encoding UTF8 index.html` |
| `brand/logotipo.jpg` | Logotipo único (circular) | No — binario |

## 15. Referencias de marca

Inspiración tomada de:
- **ElevenLabs**: Cards cálidas, tipografía audaz, sistema de elevación por contraste de superficie
- **Vercel**: Precisión técnica, whitespace extremo, tipografía limpia
- **Jeton**: Acento como personalidad de marca, gradiente como elemento signature
- **Dual-mode**: Inspirado en Stripe (alternancia claro/oscuro por sección, no por toggle)

## Cambios recientes (Jun 2026)

- **Calculadora eliminada** — La calculadora modular fue removida por confusión de precios. Ahora los precios se muestran directamente en las cards de cada plan.
- **6 testimonios implementados** — Se agregaron 6 testimonios con carrusel moderno (2 cards por página) y hover 3D suave.
- **Avatar actualizado** — Reemplazado el placeholder "AH" por avatar_aha.webp (250×250px) en la sección Sobre Mí.
- **Hero tipografía ajustada** — letter-spacing agregado al tagline para mejorar legibilidad.

