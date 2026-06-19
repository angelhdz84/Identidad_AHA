# Design Spec: Landing Page AHAguilera v2 — Rediseño

> **Fecha**: 2026-06-19
> **Estado**: Aprobado (vía brainstorming)
> **Pipeline**: Modo Design (/pro) — Fase 1 completada
> **Stack**: HTML + CSS Custom Properties + Alpine.js + Bootstrap Icons

---

## 1. Resumen

Rediseño completo de la landing page AHAguilera. Enfoque: **fondo claro + acento lime explosivo + micro-interactividad + sello visual único (código vivo + mockups de apps)**.

## 2. Decisiones de diseño (brainstorming)

| Decisión | Elección |
|----------|----------|
| Dirección visual | Claro y cercano (B) + factor memorable |
| Acento | Lime `#CFF434` con presencia fuerte sobre fondo claro |
| Elemento signature | Patrón de código hexadecimal de fondo + mockups/ilustraciones de apps |
| Interactividad | Micro-animaciones (código tipeándose, contadores scroll, hover effects) |
| Modelo de negocio | Híbrido: presentación de servicio + catálogo de apps populares con precios |
| Tipografía | Space Grotesk (headings) + Inter (body) |
| Tipo de contenido | Catálogo de servicios + apps pre-construidas + desarrollo a medida |

## 3. Estructura de secciones

1. **Hero** — Frase impactante + 2 CTAs (catálogo / consulta) + patrón código fondo
2. **Propuesta de valor** — 3 pilares: sin servidores, datos locales, doble clic
3. **Apps populares** — Grid 2x2 de apps con precios visibles
4. **Desarrollo a medida** — "¿No encuentras lo que buscas? Te lo construyo"
5. **Precios** — 3 planes: Lite $49, Standard $99, Custom $199+
6. **Cómo funciona** — 3 pasos: idea → desarrollo → descarga
7. **Stack técnico** — Logo grid (Alpine, Dexie, CryptoJS, Tailwind, DaisyUI)
8. **Comparativa** — Offline-first vs tradicional
9. **FAQ** — Acordeón con Alpine.js
10. **Sobre mí** — Bio + filosofía + foto
11. **CTA Final** — WhatsApp + Email
12. **Footer** — Links + copyright + tagline

## 4. Paleta propuesta

| Rol | Hex | Muestra |
|-----|-----|---------|
| Fondo página | `#EAF4F5` | Claro, fresco |
| Superficie cards | `#FFFFFF` | Blanco puro |
| Acento primario | `#CFF434` | Lime — CTAs, badges, highlights |
| Acento hover | `#dbf65a` | Lime más brillante |
| Texto primary | `#171614` | Casi negro, alto contraste |
| Texto secondary | `#5a6a6b` | Gris suave |
| Borde sutil | `#d0dbdc` | Gris claro |
| Borde hover | `#CFF434` | Lime en hover de cards |
| Teal (tags) | `#024653` | Badges decorativos |

## 5. Próximas fases del pipeline

- **Fase 2**: UX Research — análisis de audiencia, referencias de marca vía spec-engine
- **Fase 3**: SPEC + BRAND — spec funcional detallada + DESIGN.md
- **Fase 4**: Design System — tokens de color, tipografía, espaciado, motion
- **Fase 5**: UI Coding — código HTML/CSS/JS de la landing
- **Fase 6+**: Microcopy, Assets, Testing, Review, Deploy
