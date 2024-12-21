# Astro Starter Kit With Sass

Plantilla con de Astro v5, con sass y estructura de 
carpetas escalables para manejar de mejor manera el css
en proyectos web.

# Starter Template

Este proyecto es un **Starter Template** que proporciona una base sólida para iniciar proyectos web. El enfoque principal está en la implementación de un sistema de diseño escalable utilizando **clases de utilidad** basadas en **tokens de diseño**. Esto permite una personalización sencilla y coherente para cualquier proyecto.

## Características

1. **Clases de utilidad basadas en tokens**:
   - Los estilos están diseñados utilizando tokens de diseño centralizados (colores, tipografías, espacios, tamaños, etc.).
   - Utiliza `@use` de Sass para manejar mapas de tokens y generar clases de utilidad dinámicas.

2. **Alias de tokens**:
   - Se han definido alias que actúan como una capa semántica para mapear los tokens a conceptos específicos de diseño.

3. **Modularidad y escalabilidad**:
   - Separación de estilos en carpetas bien organizadas.
   - Compatible con diferentes temas (light, dark, etc.).

4. **Fácil personalización**:
   - Solo necesitas modificar los tokens base o alias para actualizar los estilos globales del proyecto.

5. **Listo para producción**:
   - Configuración optimizada para ser integrada fácilmente en proyectos.

## Estructura del Proyecto

```
├── src/
│   ├── styles/
│   │   ├── abstracts/        # Tokens y variables base
│   │   ├── base/             # Estilos globales como `_root.scss`
│   │   ├── components/       # Estilos específicos de componentes
│   │   └── utilities/        # Clases de utilidad generadas dinámicamente
│   └── ...                   # Otros archivos del proyecto
├── public/
├── package.json
└── ...
```

## Uso del Template

### Requisitos Previos
- [Node.js](https://nodejs.org/) instalado en tu sistema.
- Administrador de paquetes como **npm** o **yarn**.

### Instalación
1. Clona este repositorio:
   ```bash
   git clone <URL_DEL_REPOSITORIO>
   ```

2. Instala las dependencias:
   ```bash
   npm install
   ```

3. Ejecuta el proyecto en modo desarrollo:
   ```bash
   npm run dev
   ```

4. Compila para producción:
   ```bash
   npm run build
   ```

### Cómo utilizar los tokens y las clases de utilidad
1. Los tokens están definidos en los archivos dentro de `src/styles/abstracts/`.
2. Las clases de utilidad generadas automáticamente pueden ser utilizadas directamente en el HTML o como mixins en los estilos personalizados.
3. Puedes añadir nuevos tokens o modificar los existentes en `_root.scss` y las clases se actualizarán automáticamente.

### Ejemplo de clases de utilidad
```html
<div class="bg-primary-500 radius-lg p-space-m">
  Contenido con estilos basados en tokens
</div>
```
- **`bg-primary-500`**: Color de fondo principal.
- **`radius-lg`**: Bordes redondeados grandes.
- **`p-space-m`**: Espaciado de padding mediano.

## Licencia
Este proyecto está bajo la [Licencia MIT](LICENSE).



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
