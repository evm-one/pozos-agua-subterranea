# Design System Master File

> **LOGIC:** When building a specific page, first check `design-system/pages/[page-name].md`.
> If that file exists, its rules **override** this Master file.
> If not, strictly follow the rules below.

---

**Project:** Pozos de Agua Subterranea
**Generated:** 2026-08-08 15:11:57
**Category:** B2B Service

---

## Global Rules

### Color Palette

> **Fuente de verdad:** `assets/guia-visual.html`. Paleta derivada del logotipo (tierra + agua).
> Reemplaza la paleta genérica navy/gold del generador — ver "Anti-patrones de marca" al final.

| Rol | Hex | Token CSS | Uso |
|------|-----|-----------|-----|
| Tierra 700 | `#8A5A38` | `--tierra-700` | Fondos de sección oscuros (hero, franjas) |
| Tierra 500 | `#B07A4E` | `--tierra-500` | Fondos medios, texturas sutiles |
| Marfil | `#E9DFD2` | `--marfil` | Texto sobre oscuro, franjas suaves, aire cálido |
| Blanco | `#FFFFFF` | `--blanco` | Fondo dominante, tarjetas |
| Ink | `#2A2118` | `--ink` | Texto principal (nunca negro puro) |
| Café | `#5E3B22` | `--cafe` | Títulos sobre claro, footer, CTA secundario |
| Terracota | `#B5552E` | `--terracota` | Detalle cálido, eyebrows, viñetas, bordes |
| Agua 500 | `#2E7DA6` | `--agua-500` | **Acento de acción**: CTAs, enlaces, contadores |
| Agua 600 | `#256685` | `--agua-600` | Hover / pressed, labels de dato |
| WhatsApp | `#25D366` | `--wa` | Verde oficial — no forzar a la paleta |

**Proporción de uso:** 60% blanco/marfil · 30% tierra/café · 10% agua.

**Regla dura:** el azul se usa **SOLO** en CTAs, enlaces, WhatsApp y contadores.
**Nunca como fondo de sección.** El azul pierde fuerza si se usa de más, y llenar
secciones de azul saturado es exactamente lo que hace el 100% del sector.

**Color Notes:** Tierra como base, agua como foco de conversión. Un solo acento por bloque:
tierra manda, agua acentúa.

### Typography

> **Fuente de verdad:** `assets/guia-visual.html`. Reemplaza el par Lexend / Source Sans 3
> del generador, demasiado neutro para el objetivo de diferenciación.

- **Display:** una sans robusta **con carácter técnico**, vía Google Fonts.
  Candidatas: **Archivo, Sora, Barlow o Manrope**. Pesos 700–800 para H1.
- **Body:** sans neutra legible, alta legibilidad en párrafo largo.
- **PROHIBIDO:** Open Sans y Roboto. Son las fuentes de plantilla que usa todo el
  sector; adoptarlas anula la ventaja tipográfica.
- **Firma del logo:** la tipografía redondeada del logotipo se conserva solo como
  firma en header/footer. Nunca en cuerpo ni en títulos largos.

**Escala tipográfica**

| Rol | Tamaño | Peso | Color | Notas |
|-----|--------|------|-------|-------|
| Eyebrow | 12px | 700 | `--terracota` | Mayúsculas, tracking amplio (.14em) |
| H1 / Hero | 44px | 800 | `--cafe` | Line-height 1.1, letter-spacing -1px |
| H2 | 28px | 700 | `--cafe` | Misma familia display |
| Body | 16px | 400 | `--ink` | Interlineado 1.6 |
| Label / dato | 13px | 600 | `--agua-600` | Micro-pruebas, métricas (m / L/s) |

### Spacing Variables

| Token | Value | Usage |
|-------|-------|-------|
| `--space-xs` | `4px` / `0.25rem` | Tight gaps |
| `--space-sm` | `8px` / `0.5rem` | Icon gaps, inline spacing |
| `--space-md` | `16px` / `1rem` | Standard padding |
| `--space-lg` | `24px` / `1.5rem` | Section padding |
| `--space-xl` | `32px` / `2rem` | Large gaps |
| `--space-2xl` | `48px` / `3rem` | Section margins |
| `--space-3xl` | `64px` / `4rem` | Hero padding |

### Shadow Depths

| Level | Value | Usage |
|-------|-------|-------|
| `--shadow-sm` | `0 1px 2px rgba(0,0,0,0.05)` | Subtle lift |
| `--shadow-md` | `0 4px 6px rgba(0,0,0,0.1)` | Cards, buttons |
| `--shadow-lg` | `0 10px 15px rgba(0,0,0,0.1)` | Modals, dropdowns |
| `--shadow-xl` | `0 20px 25px rgba(0,0,0,0.15)` | Hero images, featured cards |

---

## Component Specs

### Buttons

> Geometría y timings del generador; colores sustituidos por los tokens de marca.

```css
/* Primary Button — acento de acción */
.btn-primary {
  background: var(--agua-500);   /* #2E7DA6 */
  color: #fff;
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}

.btn-primary:hover {
  background: var(--agua-600);   /* #256685 */
  transform: translateY(-1px);
}

/* Secondary Button — contorno café */
.btn-secondary {
  background: transparent;
  color: var(--cafe);            /* #5E3B22 */
  border: 2px solid var(--cafe);
  padding: 12px 24px;
  border-radius: 8px;
  font-weight: 600;
  transition: all 200ms ease;
  cursor: pointer;
}

.btn-secondary:hover { background: var(--cafe); color: #fff; }

/* WhatsApp — verde oficial, fuera de paleta a propósito */
.btn-wa { background: #25D366; color: #fff; }
.btn-wa:hover { background: #1DA851; }
```

### Cards

```css
.card {
  background: var(--blanco);
  border: 1px solid #E4DACD;     /* línea cálida, no gris azulado */
  border-radius: 12px;
  padding: 24px;
  box-shadow: var(--shadow-md);
  transition: all 200ms ease;
  cursor: pointer;
}

.card:hover {
  box-shadow: var(--shadow-lg);
  transform: translateY(-2px);
}
```

### Inputs

```css
.input {
  padding: 12px 16px;
  border: 1px solid #E4DACD;
  border-radius: 8px;
  font-size: 16px;              /* 16px evita el zoom automático en iOS */
  color: var(--ink);
  transition: border-color 200ms ease;
}

.input:focus {
  border-color: var(--agua-500);
  outline: none;
  box-shadow: 0 0 0 3px rgba(46, 125, 166, 0.25);
}
```

### Modals

```css
.modal-overlay {
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(4px);
}

.modal {
  background: white;
  border-radius: 16px;
  padding: 32px;
  box-shadow: var(--shadow-xl);
  max-width: 500px;
  width: 90%;
}
```

---

## Style Guidelines

**Style:** Trust & Authority

**Keywords:** Certificates/badges displayed, expert credentials, case studies with metrics, before/after comparisons, industry recognition, security badges

**Best For:** Healthcare/medical landing pages, financial services, enterprise software, premium/luxury products, legal services

**Key Effects:** Badge hover effects, metric pulse animations, certificate carousel, smooth stat reveal

### Page Pattern

**Pattern Name:** Trust & Authority + Conversion

- **Conversion Strategy:** Security badges. Case studies. Transparent pricing. Low-friction form.
- **CTA Placement:** Contact Sales / Get Quote (primary) + Nav
- **Section Order:** 1. Hero (mission/credibility), 2. Proof (logos, certs, stats), 3. Solution overview, 4. Clear CTA path

> **Adaptación al proyecto** (el patrón se conserva; solo se anota su aplicación):
> - *Security badges / certificate carousel* → **no aplica**: no hay certificaciones
>   confirmadas. Se sustituye por logos de clientes + contadores de prueba dura.
> - *Transparent pricing* → **no aplica**: proyectos cotizados a medida. Se sustituye
>   por la oferta de entrada "Diagnóstico inicial sin costo".
> - *Case studies* → tarjetas de proyecto con ubicación + profundidad (m) + gasto (L/s).
> - *Low-friction form* → 4 campos + WhatsApp flotante con mensaje pre-cargado.
> - *Get Quote (primary) + Nav* → "Solicitar cotización" en header sticky, repetido
>   tras Servicios, tras Proyectos y en el cierre.
> - El orden de 4 secciones es el esqueleto; el blueprint completo de 14 secciones
>   (competitor research §10) lo respeta y lo extiende con la línea de tiempo 1973→hoy.

---

## SIGNATURE — Motivo de marca

El logotipo es la identidad: **un círculo de agua dentro de un anillo de tierra**.
Ese motivo se reutiliza de forma sistemática como firma visual de la landing:

- **Íconos de servicio** — los 4 servicios (perforación, equipamiento, estudios,
  obras hidráulicas) se dibujan dentro de un anillo terracota con centro agua.
- **Viñetas** — listas de diferenciadores y FAQ usan el círculo concéntrico en
  lugar de un bullet o un check genérico.
- **Corte estratigráfico "del estudio a la operación"** — gráfico técnico propio
  que corta el subsuelo en capas de tierra y sitúa el agua al fondo, recorriendo
  las 5 etapas del proceso. Es el activo visual diferenciador: solo 2 de 12
  competidores usan gráficos técnicos, y ninguno tiene uno de marca.

Regla de coherencia: un solo set de íconos, trazo consistente, SVG inline.
Nunca emojis, nunca mezclar estilos de ícono.

---

## Anti-Patterns (Do NOT Use)

- ❌ Playful design
- ❌ Hidden credentials
- ❌ AI purple/pink gradients

### Additional Forbidden Patterns

- ❌ **Emojis as icons** — Use SVG icons (Heroicons, Lucide, Simple Icons)
- ❌ **Missing cursor:pointer** — All clickable elements must have cursor:pointer
- ❌ **Layout-shifting hovers** — Avoid scale transforms that shift layout
- ❌ **Low contrast text** — Maintain 4.5:1 minimum contrast ratio
- ❌ **Instant state changes** — Always use transitions (150-300ms)
- ❌ **Invisible focus states** — Focus states must be visible for a11y

### Anti-patrones de marca (específicos de este proyecto)

- ❌ **Azul como fondo de sección** — es el error visual que define al sector. El azul solo acentúa.
- ❌ **Negro puro `#000000`** — el texto va en Ink `#2A2118`.
- ❌ **Open Sans / Roboto** — fuentes de plantilla; anulan la diferenciación tipográfica.
- ❌ **Más de un acento por bloque** — tierra manda, agua acentúa.
- ❌ **Fotografía de stock** — solo fotografía real de campo, curada.
- ❌ **Hero multi-mensaje / slider** — un mensaje dominante, una prueba, un botón.
- ❌ **Badges o certificaciones sin respaldo** — nada POR VALIDAR se muestra como afirmación.

---

## Pre-Delivery Checklist

Before delivering any UI code, verify:

- [ ] No emojis used as icons (use SVG instead)
- [ ] All icons from consistent icon set (Heroicons/Lucide)
- [ ] `cursor-pointer` on all clickable elements
- [ ] Hover states with smooth transitions (150-300ms)
- [ ] Light mode: text contrast 4.5:1 minimum
- [ ] Focus states visible for keyboard navigation
- [ ] `prefers-reduced-motion` respected
- [ ] Responsive: 375px, 768px, 1024px, 1440px
- [ ] No content hidden behind fixed navbars
- [ ] No horizontal scroll on mobile
