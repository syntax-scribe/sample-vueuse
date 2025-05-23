[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useAsyncState/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `promiseTimeout` | `@vueuse/shared` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useAsyncState` | `./index` |


---

## Functions

### `p1(num: number): Promise<unknown>`

<details><summary>Code</summary>

```ts
(num = 1) => {
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve(num)
      }, 50)
    })
  }
```
</details>

- **Parameters**:
  - `num: number`
- **Return Type**: `Promise<unknown>`
- **Calls**:
  - `setTimeout`
  - `resolve`
### `p2(id: string): Promise<string>`

<details><summary>Code</summary>

```ts
async (id?: string) => {
    if (!id)
      throw new Error('error')
    return id
  }
```
</details>

- **Parameters**:
  - `id: string`
- **Return Type**: `Promise<string>`

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