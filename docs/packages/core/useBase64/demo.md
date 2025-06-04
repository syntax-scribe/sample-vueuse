[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useBase64/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useBase64` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `file` | `boolean` | let/var | `shallowRef<File>()` | ✗ |
| `image` | `boolean` | let/var | `shallowRef<HTMLImageElement>()` | ✗ |


---

## Functions

### `onFileInput(e: Event): void`

<details><summary>Code</summary>

```ts
function onFileInput(e: Event) {
  file.value = (e.target as HTMLInputElement).files![0]
}
```
</details>

- **Parameters**:
  - `e: Event`
- **Return Type**: `void`

---