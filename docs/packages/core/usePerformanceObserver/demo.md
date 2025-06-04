[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 1 |

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