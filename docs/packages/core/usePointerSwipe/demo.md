[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/usePointerSwipe/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseSwipeDirection` | `@vueuse/core` |
| `usePointerSwipe` | `@vueuse/core` |
| `computed` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `target` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |
| `container` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `reset(): void`

<details><summary>Code</summary>

```ts
function reset() {
  left.value = '0'
  opacity.value = 1
}
```
</details>

- **Return Type**: `void`

---