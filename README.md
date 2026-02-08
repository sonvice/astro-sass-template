# Astro Starter Kit — ITCSS + CUBE CSS

Starter template de Astro v5 con Sass, arquitectura **ITCSS** y filosofia **CUBE CSS**. Sistema de diseno basado en design tokens, clases de utilidad generadas automaticamente, compositions de layout sin media queries y soporte dark/light theme.

## Arquitectura CSS

La estructura sigue las capas de especificidad de ITCSS, con las compositions de CUBE CSS como capa Objects:

```
src/sass/
├── abstracts/           Settings + Tools
│   ├── tokens/          Design tokens organizados por categoria
│   │   ├── _colors       Paletas de color + mapas light/dark
│   │   ├── _typography   Font families, weights y escala fluida
│   │   ├── _spacing      Escala de espaciado con clamp()
│   │   └── _radius       Border radius
│   ├── _aliases          Tokens de componente (button, card, tag)
│   ├── _functions        px-to-rem(), token()
│   └── _mixins           breakpoint(), generate-css-variables()
│
├── base/                Generic + Elements
│   ├── _font-face        @font-face declarations
│   ├── _root             :root CSS custom properties (light + dark)
│   ├── _reset            CSS reset moderno (Andy Bell)
│   └── _global           Estilos base (body, headings, links)
│
├── compositions/        Objects (layout primitives sin media queries)
│   ├── _flow             Espaciado vertical entre hermanos
│   ├── _cluster          Flex wrap con gap
│   ├── _sidebar          Barra lateral flexible
│   ├── _switcher         2 columnas auto-stackeables
│   ├── _grid             Auto-fill responsivo con variantes
│   ├── _repel            Empuja a extremos opuestos
│   └── _wrapper          Contenedor centrado
│
├── blocks/              Components (CUBE CSS Blocks)
│   ├── _buttons          .btn con data-variant y data-size
│   ├── _cards            .card con data-variant y data-padding
│   └── _tags             .tag con data-variant
│
├── utilities/           Trumps (mayor especificidad)
│   ├── _spacing          .m-{token}, .p-{token}, .mx-{token}
│   ├── _colors           .bg-{color}-{shade}, .text-{color}-{shade}
│   ├── _text-sizes       .text-{size-token}
│   ├── _font             .ff-base, .text-bold, .text-semi-bold
│   ├── _leading          .leading-tight, .leading-normal
│   ├── _radius           .radius-{sm|md|lg|xl|full}
│   ├── _region           .region (padding de seccion)
│   ├── _flow-space       .flow-space-{token} → --flow-space
│   ├── _gutter           .gutter-{token} → --gutter
│   ├── _region-space     .region-space-{token} → --region-space
│   ├── _wrapper-width    .wrapper-narrow, .wrapper-wide
│   ├── _text-center      .text-center
│   ├── _uppercase        .uppercase
│   └── _visually-hidden  .visually-hidden
│
├── sections/            Estilos especificos de pagina
├── vendors/             CSS de terceros
└── style.scss           Punto de entrada
```

### Orden de importacion (especificidad creciente)

```scss
@use "base";          // 1. Reset, :root variables, global styles
@use "compositions";  // 2. Layout primitives (flow, cluster, grid, etc.)
@use "blocks";        // 3. UI components (button, card, tag)
@use "utilities";     // 4. Utility classes (mayor especificidad)
@use "sections";      // 5. Page-specific
@use "vendors";       // 6. Third-party
```

## Sistema de Design Tokens

Dos capas de abstraccion:

```
Tokens (por categoria) → Alias Tokens (por componente) → CSS Custom Properties
```

1. **Tokens** (`abstracts/tokens/`): Valores organizados por categoria (colors, typography, spacing, radius). Cada archivo exporta su mapa SCSS directamente.
2. **Aliases** (`abstracts/_aliases.scss`): Tokens semanticos por componente que referencian CSS custom properties con `var()`, lo que les da **reactividad automatica al cambio de tema**.

```scss
// Los alias usan var() para ser reactivos al tema
$card: (
  "bg": var(--neutral-50),     // Cambia automaticamente en dark mode
  "color": var(--neutral-900), // No necesita override manual
  "radius": var(--radius-lg),
  ...
);
```

Los alias se convierten a custom properties via:
```scss
@include generate-css-variables($card, "card-");
// Genera: --card-bg: var(--neutral-50); --card-color: var(--neutral-900); etc.
```

### CSS Custom Properties generadas en :root

| Prefijo     | Ejemplo                | Fuente          |
|:------------|:-----------------------|:----------------|
| (ninguno)   | `--neutral-50`, `--primary-200` | tokens/_colors |
| (ninguno)   | `--space-m`, `--space-xl`       | tokens/_spacing |
| (ninguno)   | `--size-0`, `--size-3`          | tokens/_typography |
| `ff-`       | `--ff-base`, `--ff-accent`      | tokens/_typography |
| `fw-`       | `--fw-bold`, `--fw-semi-bold`   | tokens/_typography |
| `radius-`   | `--radius-sm`, `--radius-full`  | tokens/_radius |

## Patron de componentes (CUBE CSS Blocks)

Basado en el articulo de [Piccalilli](https://piccalil.li/blog/how-i-build-a-button-component/):

1. **Default**: Valores base via alias tokens como custom properties
2. **Variantes**: Excepciones via `data-attributes` que solo sobreescriben lo que cambia
3. **Estados**: `:hover`, `:focus-visible`, `:active` referencian las mismas custom properties
4. **Contexto**: Componentes padres pueden inyectar valores via custom properties
5. **Tema**: Colores se adaptan automaticamente via `var()` reactivo

```html
<button class="btn" data-variant="primary" data-size="large">Accion</button>
<article class="card" data-variant="elevated">...</article>
<span class="tag" data-variant="success">Activo</span>
```

## Compositions (Layout sin media queries)

```html
<div class="flow flow-space-space-m">...</div>
<nav class="cluster gutter-space-xs">...</nav>
<div class="grid" data-layout="thirds">...</div>
<div class="sidebar"><nav>...</nav><main>...</main></div>
<header class="repel"><a href="/">Logo</a><nav class="cluster">...</nav></header>
<div class="wrapper wrapper-narrow">...</div>
```

## Uso

### Requisitos

- [Node.js](https://nodejs.org/) v18+

### Instalacion

```bash
git clone <URL_DEL_REPOSITORIO>
npm install
```

### Comandos

| Comando             | Accion                                       |
| :------------------ | :------------------------------------------- |
| `npm run dev`       | Inicia servidor de desarrollo en `localhost:4321` |
| `npm run build`     | Compila para produccion en `./dist/`          |
| `npm run preview`   | Preview del build antes de desplegar          |

### Personalizar tokens

1. Edita los valores en `src/sass/abstracts/tokens/` (archivo por categoria)
2. Las custom properties y clases de utilidad se regeneran automaticamente
3. Para agregar un componente: crea su alias en `_aliases.scss` y su block en `blocks/`

## Dependencias

- [Astro](https://astro.build/) v5
- [Sass](https://sass-lang.com/) (Dart Sass)
- [Montserrat Variable](https://fontsource.org/fonts/montserrat) via Fontsource

## Licencia

[MIT](LICENSE)
