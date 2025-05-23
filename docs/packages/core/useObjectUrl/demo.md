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
📂 **`packages/core/useObjectUrl/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useObjectUrl` | `@vueuse/core` |
| `shallowRef` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---