[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useWakeLock/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useWakeLock` | `@vueuse/core` |
| `computed` | `vue` |
| `reactive` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `onClick(): any`

<details><summary>Code</summary>

```ts
function onClick() {
  return wakeLock.isActive ? wakeLock.release() : wakeLock.request('screen')
}
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `wakeLock.release`
  - `wakeLock.request`

---