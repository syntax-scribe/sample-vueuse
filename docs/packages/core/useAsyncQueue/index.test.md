[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 5
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useAsyncQueue/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useAsyncQueue` | `./index` |


---

## Functions

### `p1(): Promise<unknown>`

<details><summary>Code</summary>

```ts
() => {
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve(1000)
      }, 10)
    })
  }
```
</details>

- **Return Type**: `Promise<unknown>`
- **Calls**:
  - `setTimeout`
  - `resolve`
### `p2(result: number): Promise<unknown>`

<details><summary>Code</summary>

```ts
(result: number) => {
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
- **Return Type**: `Promise<unknown>`
- **Calls**:
  - `setTimeout`
  - `resolve`
### `p3(result: number): Promise<unknown>`

<details><summary>Code</summary>

```ts
(result: number) => {
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve(1000 + result)
      }, 30)
    })
  }
```
</details>

- **Parameters**:
  - `result: number`
- **Return Type**: `Promise<unknown>`
- **Calls**:
  - `setTimeout`
  - `resolve`
### `pError(): Promise<unknown>`

<details><summary>Code</summary>

```ts
() => {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        reject(new Error('e'))
      }, 30)
    })
  }
```
</details>

- **Return Type**: `Promise<unknown>`
- **Calls**:
  - `setTimeout`
  - `reject`
### `abort(): void`

<details><summary>Code</summary>

```ts
() => controller.abort()
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `controller.abort`

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