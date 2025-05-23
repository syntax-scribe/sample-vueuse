[⬅️ Back to Table of Contents](../../index.md)

# 📄 `nextTick.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/.test/nextTick.ts`**

## 📦 Imports

> No imports found in this file.


---

## Functions

### `nextTwoTick(): Promise<void>`

<details><summary>Code</summary>

```ts
export function nextTwoTick() {
  return new Promise<void>((resolve) => {
    setTimeout(() => {
      setTimeout(resolve)
    })
  })
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `setTimeout`

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