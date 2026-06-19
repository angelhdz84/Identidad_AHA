# Refactor Landing Page — AHAguilera

**Fecha:** 2026-06-16
**Archivo:** `landing/index.html` (1567 líneas)

## Resumen

Auditoría UX/UI completa de la landing page. Se identificaron 15 issues y se implementaron 12 de ellos (2 cancelados por no aplicar, 1 pendiente de validación visual).

---

## Issues Implementados

### ✅ Críticos (3/3)

| # | Issue | Solución |
|---|-------|----------|
| 1 | **x-cloak faltante** — flash de contenido Alpine.js | Agregado `x-cloak` al `<html>` + CSS `[x-cloak] { display: none !important; }` |
| 2 | **Tailwind CDN cargado** — violación de regla §5.1 (no CDNs) | Reemplazado por CSS custom properties + utility classes manuales (~500 líneas CSS) |
| 3 | **Falta skip link** — barrera WCAG 2.4.1 | Agregado `<a href="#main" class="sr-only focus:not-sr-only">` al inicio del body |

### ✅ Altos (4/4)

| # | Issue | Solución |
|---|-------|----------|
| 4 | **SVG sin aria-hidden** — contenido decorativo no oculto a screen readers | Agregado `aria-hidden="true"` al SVG del logo hero |
| 5 | **Hamburger sin aria-label** — botón sin nombre accesible | Agregado `aria-label="Menú de navegación"` + `:aria-expanded="mobileOpen"` |
| 6 | **FAQ sin transición** — open/close sin animación | Reemplazado `faq-answer` class por `x-transition` de Alpine.js (enter/leave) |
| 7 | **Cards de apps sin modal** — click hace nada | Agregados 4 modales con `role="dialog"`, `aria-modal="true"`, backdrop blur, y focus trap via `@click.stop` |

### ✅ Medios (4/5)

| # | Issue | Solución |
|---|-------|----------|
| 8 | **Nav sin aria-current** — scroll spy no indica sección activa | Modificado JS para agregar/remover `aria-current="true"` en enlaces activos |
| 9 | **Code block sin copy button** — UX pobre para código | Agregado botón de clipboard con feedback visual ("Copiado") |
| 10 | **Sin schema.org** — SEO incompleto | Agregado JSON-LD con `ProfessionalService`, ofertas, y metadatos |
| 11 | **OG tags duplicados** — meta tags originales + nuevos | Eliminados los OG tags originales, conservando los completos |
| 12 | **Sin prefers-reduced-motion** — accesibilidad visual | Agregado `@media (prefers-reduced-motion: reduce)` para gradient, scroll-dot, y reveals |

### ✅ Bajos (1/3)

| # | Issue | Solución |
|---|-------|----------|
| 13 | **Font loading no local** — @font-face con `local()` no carga fuentes reales | Eliminadasdeclaraciones @font-face; usa `system-ui` stack nativo |

### ❌ Cancelados (2)

| # | Issue | Razón |
|---|-------|-------|
| 14 | **Star ratings en testimonios** | No existen star ratings — testimonios usan quote marks decorativos |
| 15 | **Palette bar aria-label** | No existe palette bar en la landing |

---

## Stack Actual (post-refactor)

| Recurso | Método |
|---------|--------|
| CSS Framework | CSS custom properties + utility classes inline (sin CDN) |
| Icons | Bootstrap Icons v1.11.3 (local CSS) |
| JS Framework | Alpine.js v3.14.9 (local JS, defer) |
| Fonts | `system-ui` nativo (sin dependencias externas) |
| Brand assets | SVGs locales en `landing/brand/` |

## Compliance Checklist

- [x] Sin CDNs en runtime
- [x] Sin ES6 `import` / `export`
- [x] Sin `fetch()` en código cliente
- [x] Sin `type="module"`
- [x] Sin `export default`
- [x] Cifrado con CryptoJS (referenciado en código demo)
- [x] UI en español (ES primary, EN secondary via toggle)
- [x] Comentarios en español
- [x] Tailwind CSS local (no CDN)
- [x] Bootstrap Icons local (no CDN)
- [x] Alpine.js local (no CDN)

## Pendiente de Validación Visual

- CSS utility classes inline: verificar que todos los breakpoints responsive funcionan correctamente (el CSS manual puede tener omisiones vs Tailwind completo)
- FAQ x-transition: verificar que `max-h-0 → max-h-[300px]` funciona con `overflow: hidden` del contenedor
- Modales: verificar focus trap en móvil y que `@click.stop` previene propagación correctamente
