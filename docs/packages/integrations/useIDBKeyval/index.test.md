[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/integrations/useIDBKeyval/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `get` | `idb-keyval` |
| `set` | `idb-keyval` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `useIDBKeyval` | `./index` |


---

## Functions

### `get(key: string): Promise<any>`

<details><summary>Code</summary>

```ts
(key: string) => Promise.resolve(cache[key])
```
</details>

- **Parameters**:
  - `key: string`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `Promise.resolve`
### `update(key: string, updater: () => any): Promise<unknown>`

<details><summary>Code</summary>

```ts
(key: string, updater: () => any) => new Promise((resolve, reject) => {
    const value = updater()
    if (value === 'error') {
      reject(new Error('update error'))
      return
    }

    cache[key] = value

    resolve(undefined)
  })
```
</details>

- **Parameters**:
  - `key: string`
  - `updater: () => any`
- **Return Type**: `Promise<unknown>`
### `del(key: string): void`

<details><summary>Code</summary>

```ts
(key: string) => {
    delete cache[key]
  }
```
</details>

- **Parameters**:
  - `key: string`
- **Return Type**: `void`
### `get(key: string): Promise<any>`

<details><summary>Code</summary>

```ts
(key: string) => Promise.resolve(cache[key])
```
</details>

- **Parameters**:
  - `key: string`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `Promise.resolve`
### `update(key: string, updater: () => any): Promise<unknown>`

<details><summary>Code</summary>

```ts
(key: string, updater: () => any) => new Promise((resolve, reject) => {
    const value = updater()
    if (value === 'error') {
      reject(new Error('update error'))
      return
    }

    cache[key] = value

    resolve(undefined)
  })
```
</details>

- **Parameters**:
  - `key: string`
  - `updater: () => any`
- **Return Type**: `Promise<unknown>`
### `del(key: string): void`

<details><summary>Code</summary>

```ts
(key: string) => {
    delete cache[key]
  }
```
</details>

- **Parameters**:
  - `key: string`
- **Return Type**: `void`

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