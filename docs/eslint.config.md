[⬅️ Back to Table of Contents](index.md)

# 📄 `eslint.config.js`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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

## 🔧 Functions

> No functions found in this file.


---