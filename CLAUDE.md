# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Build Commands

- `yarn dev` - Build CSS/JS, start livereload server, watch for changes
- `yarn test` - Validate theme with gscan (Ghost theme validator)
- `yarn zip` - Create dist/journal.zip for Ghost upload

## Architecture

Journal is a minimal newsletter theme for Ghost v5.0.0+. Key aspects:

- **Build**: Gulp 5 with PostCSS (autoprefixer, cssnano, postcss-easy-import)
- **Templating**: Handlebars (.hbs files)
- **Base styles**: Imports from `@tryghost/shared-theme-assets` - do not duplicate

### Source vs Built Files

Edit source files only:
- `assets/css/screen.css` → compiles to `assets/built/screen.css`
- `assets/js/main.js` → compiles to `assets/built/main.min.js`

Never edit files in `assets/built/` directly.

### Template Structure

- `default.hbs` - Base layout (header, nav, footer)
- `index.hbs` - Homepage with featured post, grid, sidebar
- `post.hbs`, `page.hbs` - Content templates
- `partials/loop.hbs` - Post card component
- `partials/icons/` - SVG icon partials

## Conventions

- CSS classes use `.gh-` prefix (e.g., `.gh-card`, `.gh-article`)
- Theme customization via `@custom` in templates (navigation_layout, title_font, body_font)
- Responsive images use Ghost's srcset with sizes defined in package.json `image_sizes`
- Member/subscription features use `data-portal` attributes
