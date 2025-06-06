[⬅️ Back to Table of Contents](../index.md)

# 📄 `packages.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 1 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)

## 🛠️ File Location:
📂 **`meta/packages.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `PackageManifest` | `@vueuse/metadata` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `packages` | `PackageManifest[]` | const | `[
  {
    name: 'metadata',
    display: 'Metadata for VueUse functions',
    manualImport: true,
    iife: false,
    utils: true,
    target: 'node14',
  },
  {
    name: 'shared',
    display: 'Shared utilities',
  },
  {
    name: 'core',
    display: 'VueUse',
    description: 'Collection of essential Vue Composition Utilities',
  },
  {
    name: 'components',
    display: 'Components',
    description: 'Renderless components for VueUse',
    author: 'Jacob Clevenger<https://github.com/wheatjs>',
  },
  {
    name: 'math',
    display: 'Math',
    description: 'Math functions for VueUse',
  },
  {
    name: 'nuxt',
    display: 'Nuxt',
    description: 'VueUse Nuxt Module',
    manualImport: true,
    addon: true,
    iife: false,
    utils: true,
    target: 'node14',
    external: [
      '@nuxt/kit',
      'local-pkg',
      'fs',
      'path',
      'url',
      'node:fs',
      'node:path',
      'node:url',
    ],
  },
  {
    name: 'router',
    display: 'Router',
    description: 'Utilities for vue-router',
    addon: true,
    external: [
      'vue-router',
    ],
    globals: {
      'vue-router': 'VueRouter',
    },
  },
  {
    name: 'integrations',
    display: 'Integrations',
    description: 'Integration wrappers for utility libraries',
    addon: true,
    submodules: true,
    external: [
      'axios',
      'universal-cookie',
      'qrcode',
      'http',
      'nprogress',
      'jwt-decode',
      'focus-trap',
      'change-case',
      'drauu',
      'fuse.js',
      'async-validator',
      'idb-keyval',
      'sortablejs',
      'node:http',
    ],
    globals: {
      'axios': 'axios',
      'universal-cookie': 'UniversalCookie',
      'qrcode': 'QRCode',
      'nprogress': 'nprogress',
      'jwt-decode': 'jwt_decode',
      'focus-trap': 'focusTrap',
      'drauu': 'Drauu',
      'fuse.js': 'Fuse',
      'change-case': 'changeCase',
      'async-validator': 'AsyncValidator',
      'idb-keyval': 'idbKeyval',
      'sortablejs': 'Sortable',
    },
  },
  {
    name: 'rxjs',
    display: 'RxJS',
    description: 'Enables RxJS reactive functions in Vue',
    addon: true,
    external: [
      'rxjs',
      'rxjs/operators',
    ],
    globals: {
      'rxjs': 'rxjs',
      'rxjs/operators': 'rxjs.operator',
    },
  },
  {
    name: 'firebase',
    display: 'Firebase',
    description: 'Enables realtime bindings for Firebase',
    addon: true,
    submodules: true,
    external: [
      'firebase',
      'firebase/app',
      'firebase/database',
      'firebase/firestore',
    ],
    globals: {
      'firebase': 'firebase',
      'firebase/app': 'firebase',
      'firebase/database': 'firebase',
      'firebase/firestore': 'firebase',
    },
  },
  {
    name: 'electron',
    display: 'Electron',
    description: 'Electron renderer process modules for VueUse',
    author: 'Archer Gu<https://github.com/ArcherGu>',
    addon: true,
    external: [
      'electron',
    ],
    iife: false,
  },
]` | ✓ |


---