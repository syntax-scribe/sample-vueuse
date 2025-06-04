[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useScroll/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useScroll` | `@vueuse/core` |
| `computed` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `toRefs` | `vue` |
| `useTemplateRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `el` | `boolean` | let/var | `useTemplateRef<HTMLElement>('el')` | ✗ |
| `height` | `number` | let/var | `shallowRef<'h-[500px]' | 'h-[200px]'>('h-[500px]')` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `updateScrollPosition(): void`

<details><summary>Code</summary>

```ts
function updateScrollPosition() {
  height.value = height.value === 'h-[500px]' ? 'h-[200px]' : 'h-[500px]'
  nextTick(() => {
    measure()
  })
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `nextTick (from vue)`
  - `measure`

---