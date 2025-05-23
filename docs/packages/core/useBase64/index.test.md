[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useBase64/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `useBase64` | `./index` |


---

## Functions

### `serializer(arr: number[]): string`

<details><summary>Code</summary>

```ts
(arr: number[]) => {
      return JSON.stringify(arr.map(el => el * 2))
    }
```
</details>

- **Parameters**:
  - `arr: number[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
  - `arr.map`

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