# spec: landing-v2

## 1. Descripción general

**Landing page profesional** para AHAguilera — desarrollador freelance de apps offline-first. 
Un híbrido entre catálogo de productos y presentación de servicios.

- **Audiencia**: Mipymes latinoamericanas, freelancers, emprendedores no técnicos
- **Problema que resuelve**: Dueños de negocio que necesitan apps funcionales sin pagar servidores ni depender de internet
- **Propuesta única**: Apps que se abren con doble clic, funcionan sin internet, y los datos son 100% del usuario

## 2. Stack técnico

| Tecnología | Rol | Archivo |
|-----------|-----|---------|
| CSS Custom Properties | Sistema de diseño | En `index.html` |
| Alpine.js 3.x | Reactividad (toggle, acordeón, dark mode, lang) | `assets/js/libs/alpine.js` |
| Bootstrap Icons | Iconos SVG | `assets/css/bootstrap-icons.css` |
| Inter Variable | Tipografía principal | `assets/fonts/InterVariable.woff2` |

**Prohibiciones** (stack compliance):
- ❌ Sin CDNs, sin `import`/`export`, sin `fetch()`, sin `type="module"`
- ❌ Sin Tailwind/DaisyUI (usamos CSS nativo con custom properties)
- ✅ Rutas relativas siempre (`./assets/...`)

## 3. Secciones / Módulos

La landing es de UNA página, no tiene módulos separados. Las secciones son:

| # | Sección | Componentes clave | Alpine.js |
|---|---------|------------------|-----------|
| 1 | Nav | Logo wordmark, links, toggle ES/EN | `x-data`, `x-model` lang |
| 2 | Hero | Headline, subheadline, 2 CTAs, patrón código fondo | — |
| 3 | Propuesta de valor | 3 cards con iconos + hover lime | Intersection Observer |
| 4 | Apps populares | Grid 2×2 apps con precio + badge | Modales x-show |
| 5 | Desarrollo a medida | CTA a consulta personalizada | — |
| 6 | Precios | 3 planes (Lite $49, Std $99⭐, Custom $199+) | — |
| 7 | Cómo funciona | 3 pasos verticales con línea conectora | Intersection Observer |
| 8 | Stack técnico | Logo grid Alpine, Dexie, CryptoJS, Tailwind, DaisyUI | — |
| 9 | Comparativa | Tabla offline-first vs tradicional | Stagger animation |
| 10 | FAQ | 6 preguntas acordeón | `x-show` + `x-transition` |
| 11 | Sobre mí | Foto, bio, skills badges | — |
| 12 | CTA Final | WhatsApp + Email con íconos grandes | — |
| 13 | Footer | Logo, links, tagline | — |

## 4. Flujos de usuario

### Flujo principal: Visitante → Cliente
1. Llega a la landing
2. Ve hero → entiende propuesta de valor en segundos
3. Scrollea a Apps Populares → ve precios
4. Si le interesa una app → clic "Comprar" → WhatsApp directo
5. Si no encuentra lo que busca → clic "Desarrollo a medida" → WhatsApp
6. Scrollea FAQ para resolver dudas
7. CTA Final → WhatsApp o Email

### Flujo secundario: Visitante escéptico
1. Llega y duda → scrollea "Cómo funciona" + "Stack técnico"
2. Ve la Comparativa offline-first vs tradicional
3. Lee "Sobre mí" para generar confianza
4. FAQ resuelve objeciones
5. CTA Final

## 5. Reglas de negocio

- Los precios son fijos y visibles (sin "cotización")
- Los planes Lite/Standard tienen features delimitados
- Custom es elástico: "dime tu idea y te presupuesto"
- Todos los CTAs principales → WhatsApp (primario) o Email (alternativo)
- No hay carrito de compras, no hay checkout online → lead generation vía WhatsApp

## 6. Perfil

**Lite** — La landing es 100% frontend estático. Sin base de datos, sin backend.

## 7. Brand Voice (inspirado ElevenLabs + Vercel + Jeton)

| Atributo | Cómo se manifiesta |
|----------|-------------------|
| **Cercano pero profesional** | "Tu app funciona sin internet" no "solución cloud-agnostic offline-capable" |
| **Directo, sin rodeos** | Frases cortas. Sin párrafos de relleno |
| **En español hispano** | "Doble clic y funciona" — no "double click and it works" |
| **Confianza silenciosa** | El código habla. No necesita testimonios falsos ni sellos |
| **Lime como identidad** | El acento `#CFF434` es parte del discurso visual |

## 8. Brand Narrative

**Tesis central**: La mejor infraestructura es la que no existe.

**Historia**: AHAguilera nace de una convicción — el software debería liberar, no esclavizar. Mientras la industria corre hacia más complejidad, AHAguilera corre hacia menos. Tus datos en tu máquina. Tu app en tu escritorio. Sin mensualidades, sin servidores, sin que te vendan "la nube" como única opción.

**Tagline**: "Apps que funcionan sin internet. Sin servidores. Sin complicaciones."

## 9. Design Principles

1. **Claridad sobre creatividad** — Cada elemento tiene un propósito. Sin decoración vacía.
2. **Menos es más** — Whitespace generoso. Una idea por sección.
3. **El acento lime es voz, no ruido** — Aparece en CTAs, transiciones, highlights. Máximo 10% del área visual.
4. **Micro-interactividad con sentido** — Las animaciones explican (fade-in = aparece, hover = es interactivo). No se anima por animar.
5. **Mobile-first** — Todo funciona en móvil. Touch targets ≥ 44px.

## 10. Personas

| Persona | Descripción | Comportamiento |
|---------|------------|----------------|
| **María, Mipyme** | Dueña de tienda física, 45 años, no técnica | Quiere llevar inventario sin pagar internet. Scrollea lento, lee todo. Confía si ve "sin internet" |
| **Carlos, Freelancer** | Contador, 30 años, algo técnico | Busca apps de presupuesto. Compara precios. Valora privacidad. Llega a la sección de precios directo |
| **Ana, Emprendedora** | 28 años, varios proyectos | Necesita apps rápidas sin compromiso. Quiere ver ejemplos y precios claros antes de contactar |

## 11. States

| Estado | Estrategia |
|--------|-----------|
| Loading | Skeleton con shimmer en gradiente de lime suave |
| Empty | No aplica (landing estática sin datos dinámicos) |
| Error | Si Alpine.js no carga, el HTML estático es funcional (progressive enhancement) |
| Hover | Cards: borde lime `#CFF434`. CTAs: lime más brillante `#dbf65a`. Nav links: color lime |
| Focus | `outline: 2px solid #CFF434; outline-offset: 2px` |
| Active/Click | Scale sutil `transform: scale(0.98)` |

## 12. Motion Design

| Elemento | Animación | Timing | Easing |
|----------|-----------|--------|--------|
| Hero headline | fadeIn + translateY(20→0) | 600ms | cubic-bezier(0.16, 1, 0.3, 1) |
| Secciones al scroll | fadeIn + translateY(30→0) | 500ms | ease-out |
| Cards hover | border-color + translateY(-2px) | 200ms | ease-out |
| Tarjetas de apps | Stagger: i × 100ms | 300ms c/u | ease-out |
| FAQ toggle | height + opacity | 300ms | ease-out |
| CTA hover | scale(1.02) + brighter lime | 150ms | ease-out |
| Patrón código fondo | static (no animado) | — | — |

## 13. Librerías adicionales

Ninguna. Stack mínimo: Alpine.js + Bootstrap Icons + Inter font local.

## 14. Referencias de marca

Inspiración tomada de:
- **ElevenLabs**: Cards cálidas, tipografía audaz, sistema de elevación por contraste de superficie
- **Vercel**: Precisión técnica, whitespace extremo, tipografía limpia
- **Jeton**: Acento como personalidad de marca, gradiente como elemento signature

