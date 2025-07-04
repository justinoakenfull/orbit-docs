---
title: React Structure - default
description: React default structure
published: true
date: 2025-06-26T06:35:22.722Z
tags: design, react, learning, resources, structure
editor: markdown
dateCreated: 2025-06-26T02:57:31.953Z
---

## Project File Structure Overview

Below is a breakdown of each top-level file and folder in your React Native (Expo) project, with a brief description of its purpose.

---

### `.expo/`
- **README.md**  
  Notes about the local Expo setup and tooling.

- **devices.json**  
  Tracks connected devices (emulators, physical devices) for the Expo dev server.

- **types/router.d.ts**  
  TypeScript definitions for Expo Router (provides strong typing for your route files).

- **web/cache/production/images/favicon/...**  
  Cached, fingerprinted favicon assets used when you build the web version of your app.

---

### `.gitignore`
Lists files and folders (e.g. `node_modules/`, build outputs) that Git should ignore.

---

### `.vscode/`
- **settings.json**  
  VS Code workspace settings (e.g. formatter, linter rules) scoped to this project.

---

### `README.md`
A markdown overview of your project—how to install dependencies, run the app, and any important notes.

---

### `app/`
Houses your Expo Router–based screens and layouts.
- **_layout.tsx** (root)  
  Defines the base layout (e.g. shared header, footer or background) for all routes under `app/`.
- **(tabs)/_layout.tsx**  
  Layout for your bottom/tab navigation area.
- **(tabs)/index.tsx**  
  The “home” screen shown in the default tab.
- **(tabs)/explore.tsx**  
  A second tab screen (e.g. “Explore”).
- **+not-found.tsx**  
  Fallback UI when the user navigates to an undefined route.

---

### `app.json`
Expo configuration file (app slug, SDK version, splash screen settings, deep-linking config).

---

### `assets/`
- **fonts/**  
  Custom font files (e.g. `SpaceMono-Regular.ttf`) to be linked into your app.
- **images/**  
  Icons, splash images, and any other static image assets.

---

### `components/`
Reusable UI elements used throughout your app.
- **Collapsible.tsx**, **ParallaxScrollView.tsx**, etc.  
  Self-contained components implementing specific behaviors.
- **ui/**  
  Platform-specific versions of shared components (e.g. `TabBarBackground.ios.tsx` vs. `TabBarBackground.tsx`).

---

### `constants/`
- **Colors.ts**  
  Centralized color palette for light/dark modes or theme variants.

---

### `eslint.config.js`
JavaScript file exporting your ESLint rules and plugins for linting your code.

---

### `expo-env.d.ts`
TypeScript declarations auto-generated by Expo to help with environment variables and global types.

---

### `hooks/`
Custom React hooks for theming and color schemes.
- **useColorScheme.ts**, **useThemeColor.ts**  
  Abstract away platform/dark-mode logic so your components can stay clean.

---

### `package.json` & `package-lock.json`
- **package.json**  
  Lists your project’s dependencies, scripts (e.g. `start`, `build`), and metadata.
- **package-lock.json**  
  Exact dependency tree lockfile to ensure consistent installs.

---

### `printTree.js`
The Node.js script you added to generate this file structure listing.

---

### `scripts/`
- **reset-project.js**  
  Custom script (perhaps to clear caches, reinstall dependencies, or reset simulators).

---

### `structure.txt`
The raw output of running `node printTree.js > structure.txt` (for reference).

---

### `tsconfig.json`
TypeScript compiler options (module resolution, strictness flags, JSX support) for the entire project.

---

That covers every major folder and file.
