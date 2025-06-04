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
📂 **`packages/core/useObjectUrl/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useObjectUrl` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `target` | `HTMLInputElement` | let/var | `e.target as HTMLInputElement` | ✗ |
| `files` | `FileList` | let/var | `target.files` | ✗ |


---

## Functions

### `onFileChange(e: Event): void`

<details><summary>Code</summary>

```ts
function onFileChange(e: Event) {
  const target = e.target as HTMLInputElement
  const files = target.files
  file.value = (files && files.length > 0) ? files[0] : undefined
}
```
</details>

- **Parameters**:
  - `e: Event`
- **Return Type**: `void`

---