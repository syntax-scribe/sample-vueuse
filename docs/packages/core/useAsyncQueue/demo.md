[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 1
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useAsyncQueue/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useAsyncQueue` | `@vueuse/core` |


---

## Functions

### `p1(): Promise<any>`

<details><summary>Code</summary>

```ts
function p1() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(1000)
    }, 10)
  })
}
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `setTimeout`
  - `resolve`
### `p2(result: number): Promise<any>`

<details><summary>Code</summary>

```ts
function p2(result: number) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(1000 + result)
    }, 20)
  })
}
```
</details>

- **Parameters**:
  - `result: number`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `setTimeout`
  - `resolve`

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