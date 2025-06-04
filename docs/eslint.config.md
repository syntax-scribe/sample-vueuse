[⬅️ Back to Table of Contents](index.md)

# 📄 `eslint.config.js`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)

## 🛠️ File Location:
📂 **`eslint.config.js`**

## 📦 Imports

| Name | Source |
|------|--------|
| `resolve` | `node:path` |
| `fileURLToPath` | `node:url` |
| `antfu` | `@antfu/eslint-config` |
| `createSimplePlugin` | `eslint-factory` |
| `createAutoInsert` | `eslint-plugin-unimport` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `restricted` | `(string | { name: string; importNames: string[]; })[]` | let/var | `[
  'vue-demi',
  '@vue/reactivity',
  '@vue/runtime-core',
  '@vue/runtime-dom',
  '@vue/composition-api',
  '..',
  '../..',
  resolve(dir, 'packages/core/index.ts'),
  resolve(dir, 'packages/shared/index.ts'),
  {
    name: 'vue',
    importNames: ['onMounted', 'onUnmounted', 'unref', 'toRef'],
  },
]` | ✗ |


---