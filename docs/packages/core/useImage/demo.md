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
📂 **`packages/core/useImage/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useImage` | `@vueuse/core` |
| `deepRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `colors` | `string[]` | const | `['fff', '000', '5f0caa']` | ✗ |
| `color` | `string` | const | `colors[Math.floor(Math.random() * colors.length)]` | ✗ |


---

## Functions

### `change(): void`

<details><summary>Code</summary>

```ts
function change() {
  imageOptions.value.src = ''
  const color: string = colors[Math.floor(Math.random() * colors.length)]
  imageOptions.value.src = `https://place-hold.it/300x200/${color}`
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `Math.floor`
  - `Math.random`

---