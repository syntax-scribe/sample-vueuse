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
📂 **`packages/core/useImage/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useImage` | `@vueuse/core` |
| `deepRef` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---