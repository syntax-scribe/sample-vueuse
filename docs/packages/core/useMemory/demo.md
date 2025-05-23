[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 1
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useMemory/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useMemory` | `@vueuse/core` |


---

## Functions

### `size(v: number): string`

<details><summary>Code</summary>

```ts
function size(v: number) {
  const kb = v / 1024 / 1024
  return `${kb.toFixed(2)} MB`
}
```
</details>

- **Parameters**:
  - `v: number`
- **Return Type**: `string`
- **Calls**:
  - `kb.toFixed`

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