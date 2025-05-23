[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useOffsetPagination/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useOffsetPagination` | `@vueuse/core` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |


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

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---