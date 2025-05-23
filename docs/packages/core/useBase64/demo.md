[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useBase64/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useBase64` | `@vueuse/core` |
| `shallowRef` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---