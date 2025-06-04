[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useElementHover/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `vElementHover` | `@vueuse/components` |
| `useElementHover` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `el` | `boolean` | let/var | `useTemplateRef<HTMLButtonElement>('el')` | ✗ |


---

## Functions

### `onHover(hovered: boolean): void`

<details><summary>Code</summary>

```ts
function onHover(hovered: boolean) {
  isDirectiveHovered.value = hovered
}
```
</details>

- **Parameters**:
  - `hovered: boolean`
- **Return Type**: `void`

---