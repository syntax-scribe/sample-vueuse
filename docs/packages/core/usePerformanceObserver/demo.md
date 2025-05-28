[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
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
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/usePerformanceObserver/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `usePerformanceObserver` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `entrys` | `boolean` | let/var | `shallowRef<PerformanceEntry[]>([])` | ✗ |


---

## Functions

### `refresh(): void`

<details><summary>Code</summary>

```ts
function refresh() {
  return window.location.reload()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `window.location.reload`

---