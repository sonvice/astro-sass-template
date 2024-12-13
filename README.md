# Astro Starter Kit With Sass

Plantilla con de Astro v5, con sass y estructura de 
carpetas escalables para manejar de mejor manera el css
en proyectos web.

# Clases de Utilidad Generadas

Este documento describe las clases de utilidad generadas en los archivos `_font.scss`, `_spacing.scss`, `_text-sizes.scss`, y `colors`. Estas clases te permiten aplicar estilos comunes directamente en tu HTML sin necesidad de escribir CSS adicional.

---

## **1. Tipografía (`_font.scss`):**
Clases relacionadas con familias tipográficas y pesos de fuente.

### **Familias Tipográficas**
```css
.font-base {
  font-family: var(--font-family-base);
}

.font-accent {
  font-family: var(--font-family-accent);
}
```

### **Pesos de Fuente**
```css
.fw-default {
  font-weight: var(--font-weight-default);
}

.fw-semi-bold {
  font-weight: var(--font-weight-semi-bold);
}

.fw-bold {
  font-weight: var(--font-weight-bold);
}
```

---

## **2. Espaciado (`_spacing.scss`):**
Clases generadas a partir del mapa `$spaces`. Estas clases permiten agregar márgenes y padding con valores predefinidos.

### **Clases de Márgenes**
```css
.m-[size] {
  margin: var(--space-[size]);
}

.mt-[size] {
  margin-top: var(--space-[size]);
}

.mr-[size] {
  margin-right: var(--space-[size]);
}

.mb-[size] {
  margin-bottom: var(--space-[size]);
}

.ml-[size] {
  margin-left: var(--space-[size]);
}

.mx-[size] {
  margin-left: var(--space-[size]);
  margin-right: var(--space-[size]);
}

.my-[size] {
  margin-top: var(--space-[size]);
  margin-bottom: var(--space-[size]);
}
```

### **Clases de Padding**
```css
.p-[size] {
  padding: var(--space-[size]);
}

.pt-[size] {
  padding-top: var(--space-[size]);
}

.pr-[size] {
  padding-right: var(--space-[size]);
}

.pb-[size] {
  padding-bottom: var(--space-[size]);
}

.pl-[size] {
  padding-left: var(--space-[size]);
}

.px-[size] {
  padding-left: var(--space-[size]);
  padding-right: var(--space-[size]);
}

.py-[size] {
  padding-top: var(--space-[size]);
  padding-bottom: var(--space-[size]);
}
```

---

## **3. Tamaños Tipográficos (`_text-sizes.scss`):**
Clases generadas a partir del mapa `$text-sizes` para aplicar tamaños predefinidos de fuente.

### **Clases de Tamaño de Texto**
```css
.text-[size] {
  font-size: var(--text-size-[size]);
}
```
Ejemplo:
```html
<p class="text-size-0">Texto con tamaño 0</p>
<p class="text-size-1">Texto con tamaño 1</p>
```

---

## **4. Colores (`colors`):**
Clases para aplicar colores a fondo y texto generadas a partir del mapa `$light`.

### **Colores de Fondo**
```css
.bg-[color]-[shade] {
  background-color: var(--[color]-[shade]);
}
```

### **Colores de Texto**
```css
.color-[color]-[shade] {
  color: var(--[color]-[shade]);
}
```

Ejemplo:
```html
<div class="bg-primary-100 color-primary-700">
  Fondo con color primario 100 y texto primario 700
</div>
```

---

## **Notas Adicionales**
- **Nomenclatura Dinámica:** Reemplaza `[size]`, `[color]`, y `[shade]` con los valores definidos en los mapas de tu configuración.
- **Modo Oscuro:** Si está habilitado, los colores para el tema oscuro serán gestionados automáticamente mediante las variables CSS dentro de una media query.

---


## 🧞 Commands

All commands are run from the root of the project, from a terminal:

| Command                   | Action                                           |
| :------------------------ | :----------------------------------------------- |
| `npm install`             | Installs dependencies                            |
| `npm run dev`             | Starts local dev server at `localhost:4321`      |
| `npm run build`           | Build your production site to `./dist/`          |
| `npm run preview`         | Preview your build locally, before deploying     |
| `npm run astro ...`       | Run CLI commands like `astro add`, `astro check` |
| `npm run astro -- --help` | Get help using the Astro CLI                     |

## 👀 Want to learn more?

Feel free to check [our documentation](https://docs.astro.build) or jump into our [Discord server](https://astro.build/chat).
