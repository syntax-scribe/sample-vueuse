[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 7 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)

## 🛠️ File Location:
📂 **`packages/core/useMousePressed/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `reactify` | `@vueuse/core` |
| `useMousePressed` | `@vueuse/core` |
| `useToggle` | `@vueuse/core` |
| `computed` | `vue` |
| `reactive` | `vue` |
| `useTemplateRef` | `vue` |
| `YAML` | `yaml` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `el` | `boolean` | let/var | `useTemplateRef<HTMLElement>('el')` | ✗ |
| `target` | `number` | let/var | `computed<HTMLElement | null>(() =>
  (withTarget.value ? el.value : window) as HTMLElement)` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |


---