# Guía de Marca — AHAguilera

> **Identidad visual para desarrollo freelance moderno**
> Versión 1.0

---

## 1. Logo

### 1.1 Variantes

| Variante | Archivo | Uso |
|----------|---------|-----|
| **Icono** | `logo-icon.svg` | Favicon, app icon, avatar, favicon, social media avatar |
| **Wordmark** | `logo-wordmark.svg` | Header web, documentos, firma de email |
| **Completo** | `logo-full.svg` | Landing page, presentaciones, marketing |

### 1.2 Composición wordmark

```
AHAguilera
^ ^       ^
| |       |
A=neón    guilera=blanco hielo
H=blanco  Subtítulo=teal
```

- **AHA**: `#CFF434` (neón) — peso 800
- **guilera**: `#EAF4F5` (blanco hielo) — peso 400
- **Línea acento**: `#07D16E` (verde) bajo las iniciales
- **Tagline**: `#024653` (teal) en caps con letter-spacing

### 1.3 Espacio mínimo

Mantener un área de seguridad igual al 20% del alto del logo alrededor de todos los lados.

### 1.4 Tamaños mínimos

| Variante | Digital | Print |
|----------|---------|-------|
| Icono | 24px | 0.25in |
| Wordmark | 120px | 1in |
| Completo | 200px | 1.5in |

### 1.5 Usos incorrectos

- No cambiar colores del logo
- No rotar, distorsionar o estirar
- No agregar sombras, gradientes ni efectos
- No colocar sobre fondos que compitan con el contraste
- No separar el icono del wordmark en el logo completo
- No usar la línea de acento como elemento decorativo independiente

### 1.6 Fondos

| Fondo | Logo | Visibilidad |
|-------|------|-------------|
| `#171614` | wordmark completo | ✅ Óptimo |
| `#024653` | wordmark | ✅ Bueno |
| Blanco/gris claro | icono sobre teal, o wordmark sobre acento | ✅ Usar full con icono |
| Sobre imagen | icono con fondo teal | ✅ |

---

## 2. Color

### 2.1 Paleta base

| Token | Hex | Muestra | Rol |
|-------|-----|---------|-----|
| `--surface` | `#171614` | ████ | Fondo principal |
| `--surface-elevated` | `#1f1d1a` | ████ | Cards, modales |
| `--text-primary` | `#EAF4F5` | ████ | Texto sobre dark |
| `--text-secondary` | `#9ba8a9` | ████ | Texto secundario |
| `--accent` | `#CFF434` | ████ | CTAs, links, highlights |
| `--accent-secondary` | `#07D16E` | ████ | Éxito, badges |
| `--surface-teal` | `#024653` | ████ | Secciones destacadas |
| `--border` | `#2a2824` | ████ | Bordes |

### 2.2 Jerarquía de color

El acento neón `#CFF434` es el color más distintivo de la marca. Debe usarse con moderación para mantener su impacto. Regla general: **menos del 10% de cualquier superficie** debe usar el acento primario.

| Elemento | Color |
|----------|-------|
| Botón primario (CTA) | `#CFF434` con texto `#171614` |
| Botón secundario | Borde `#CFF434` sobre fondo transparente |
| Links | `#CFF434` subrayado |
| Botón éxito | `#07D16E` |
| Tags | Fondo `#024653`, texto `#EAF4F5` |
| Cards | Fondo `#1f1d1a` |
| Bordes | `#2a2824` |

### 2.3 Tema claro

| Token original | Equivalente claro |
|----------------|-------------------|
| `#171614` | `#EAF4F5` |
| `#1f1d1a` | `#ffffff` |
| `#EAF4F5` | `#171614` |

Los acentos (`#CFF434`, `#07D16E`, `#024653`) se mantienen igual en ambos temas.

---

## 3. Tipografía

### 3.1 Familias

| Rol | Fuente | Peso | Alternativa |
|-----|--------|------|-------------|
| UI / Headings | **Inter** | 400, 500, 600, 700, 800 | system-ui |
| Body | **Inter** | 400, 500 | system-ui |
| Código | **JetBrains Mono** | 400, 600 | 'Courier New' |
| Display (hero) | **Space Grotesk** | 500, 700 | Inter |

### 3.2 Escala tipográfica

| Nivel | Tamaño | Peso | Leading | Tracking |
|-------|--------|------|---------|----------|
| Display | 72px / clamp(3rem, 5vw, 4.5rem) | 700 | 1.0 | -0.03em |
| H1 | 48px / 3rem | 700 | 1.1 | -0.02em |
| H2 | 36px / 2.25rem | 700 | 1.15 | -0.015em |
| H3 | 28px / 1.75rem | 600 | 1.2 | -0.01em |
| Body | 16px / 1rem | 400 | 1.6 | 0 |
| Small | 14px / 0.875rem | 400 | 1.5 | 0 |
| Caption | 12px / 0.75rem | 500 | 1.4 | 0.02em |
| Tagline | 11-13px | 500 | 1 | 0.25-0.3em |

### 3.3 Reglas

- Body mínimo 16px. Máximo 64ch por línea.
- Usar `rem`. Nunca `px` en font-size.
- Una familia (Inter) basta. Pesos variados crean jerarquía.
- Tagline siempre en caps con letter-spacing amplio.
- Código siempre en JetBrains Mono.

---

## 4. Voz y Tono

### 4.1 Personalidad

| Atributo | Cómo se manifiesta |
|----------|-------------------|
| **Técnico pero accesible** | Explica conceptos sin jargon innecesario |
| **Directo, sin relleno** | Respuestas concisas. Sin introducciones ni conclusiones |
| **En español siempre** | UI, docs, variables, commits |
| **Freelance profesional** | Cada entrega es producto terminado, no prototipo |
| **Confianza silenciosa** | No necesita adornos. El código habla |

### 4.2 Ejemplos

| Contexto | Correcto | Incorrecto |
|----------|----------|------------|
| Hero | "Apps que funcionan sin internet" | "Soluciones cloud-native con arquitectura serverless" |
| CTA | "Empezar ahora" | "Iniciar prueba gratuita de 30 días" |
| Error | "No se pudo guardar. Reintenta." | "Ha ocurrido un error inesperado en la operación" |
| Descripción | "Dexie guarda en IndexedDB" | "Wrapper de object stores con promisificación" |

---

## 5. Aplicaciones

### 5.1 Header web

```
[Icono AHA] AHAguilera  |  Proyectos  Servicios  Contacto  [CTA]
```

- Logo wordmark a la izquierda
- Nav links en `#EAF4F5` con hover `#CFF434`
- CTA botón `#CFF434` texto `#171614`

### 5.2 Favicon

Usar `logo-icon.svg` renderizado a:
- 16×16, 32×32, 48×48 (favicon tradicional)
- 96×96, 180×180 (app icons, apple-touch-icon)

### 5.3 Documentación

- Encabezado: logo wordmark + breadcrumbs
- Títulos en Inter Bold
- Código en JetBrains Mono sobre `#1f1d1a`
- Tablas con borde `#2a2824`

### 5.4 Redes sociales

- Avatar: logo-icon sobre fondo `#024653` (cuadrado)
- Banner: logo-full sobre gradiente sutil `#171614` → `#024653`

---

## 6. Assets incluidos

```
brand/
├── logo-icon.svg        # Solo icono (favicon, avatar)
├── logo-wordmark.svg    # Marca textual (header, docs)
├── logo-full.svg        # Completo (landing, presentaciones)
├── palette.json         # Tokens de color completos
└── guidelines.md        # Esta guía
```

---

> **AHAguilera** — Identidad visual v1.0
> Paleta: `#171614` `#CFF434` `#EAF4F5` `#024653` `#07D16E`
