[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 2 |
| ⚡ Async/Await Patterns | 4 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `controller` | `AbortController` | let/var | `new AbortController()` | ✗ |
| `controller` | `AbortController` | let/var | `new AbortController()` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `p1` | *none* | new Promise(...) |
| promise-chain | `p2` | *none* | new Promise(...) |
| promise-chain | `p3` | *none* | new Promise(...) |
| promise-chain | `pError` | *none* | new Promise(...) |


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