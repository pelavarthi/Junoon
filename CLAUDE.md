# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Junoon is a mobile application built with Ionic Framework and Angular, using Capacitor for native iOS deployment. The app ID is `com.junoon.app`.

## Tech Stack

- **Framework**: Angular 20 with Ionic 8
- **Mobile Runtime**: Capacitor 8 (iOS)
- **Styling**: SCSS with Ionic theming
- **Testing**: Karma + Jasmine
- **Linting**: ESLint with Angular-specific rules

## Common Commands

```bash
# Development server (http://localhost:4200)
npm start

# Production build (outputs to www/)
npm run build

# Run unit tests
npm test

# Lint code
npm run lint

# Watch mode for development
npm run watch
```

### iOS Development

```bash
# Sync web assets to iOS project
npx cap sync ios

# Open in Xcode
npx cap open ios
```

## Architecture

### Module Structure

The app uses Angular's NgModule pattern with lazy-loaded feature modules:

- `src/app/app.module.ts` - Root module bootstrapping IonicModule and AppRoutingModule
- `src/app/app-routing.module.ts` - Root router with lazy-loaded routes
- Feature modules follow the pattern: `src/app/<feature>/<feature>.module.ts`

### Routing

Routes use lazy loading with `loadChildren`:
```typescript
loadChildren: () => import('./feature/feature.module').then(m => m.FeaturePageModule)
```

### Component Conventions

- Components use `standalone: false` (NgModule-based)
- Component selectors must use `app-` prefix in kebab-case
- Component classes must be suffixed with `Page` or `Component`
- Directive selectors use `app` prefix in camelCase

### Theming

- Global styles: `src/global.scss`
- Ionic CSS variables: `src/theme/variables.scss`
- Component styles use SCSS (`.scss` extension)

### Build Output

- Development build outputs to `www/`
- Production uses file hashing and environment replacement via `src/environments/`
