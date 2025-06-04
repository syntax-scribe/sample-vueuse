[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 4 |
| ⚡ Async/Await Patterns | 2 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useOffsetPagination/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useOffsetPagination` | `@vueuse/core` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `database` | `boolean` | let/var | `deepRef<User[]>([])` | ✗ |
| `start` | `number` | let/var | `(page - 1) * pageSize` | ✗ |
| `end` | `number` | let/var | `start + pageSize` | ✗ |
| `data` | `boolean` | let/var | `deepRef<User[]>([])` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `fetch` | *none* | new Promise(...) |
| promise-chain | `fetchData` | *none* | fetch(currentPage, currentPageSize).then |


---

## Functions

### `fetch(page: number, pageSize: number): boolean`

<details><summary>Code</summary>

```ts
function fetch(page: number, pageSize: number) {
  return new Promise<User[]>((resolve, reject) => {
    const start = (page - 1) * pageSize
    const end = start + pageSize
    setTimeout(() => {
      resolve(database.value.slice(start, end))
    }, 100)
  })
}
```
</details>

- **Parameters**:
  - `page: number`
  - `pageSize: number`
- **Return Type**: `boolean`
- **Calls**:
  - `setTimeout`
  - `resolve`
  - `database.value.slice`
### `fetchData({ currentPage, currentPageSize }: { currentPage: number, currentPageSize: number }): void`

<details><summary>Code</summary>

```ts
function fetchData({ currentPage, currentPageSize }: { currentPage: number, currentPageSize: number }) {
  fetch(currentPage, currentPageSize).then((responseData) => {
    data.value = responseData
  })
}
```
</details>

- **Parameters**:
  - `{ currentPage, currentPageSize }: { currentPage: number, currentPageSize: number }`
- **Return Type**: `void`
- **Calls**:
  - `fetch(currentPage, currentPageSize).then`

---

## Interfaces

### `User`

<details><summary>Interface Code</summary>

```ts
interface User {
  id: number
  name: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `id` | `number` | ✗ |  |
| `name` | `string` | ✗ |  |


---