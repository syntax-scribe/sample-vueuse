[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 5 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `cache` | `any` | const | `{} as any` | ✗ |
| `KEY1` | `"vue-use-idb-keyval-1"` | const | `'vue-use-idb-keyval-1'` | ✗ |
| `KEY2` | `"vue-use-idb-keyval-2"` | const | `'vue-use-idb-keyval-2'` | ✗ |
| `KEY3` | `"vue-use-idb-keyval-3"` | const | `'vue-use-idb-keyval-3'` | ✗ |
| `KEY4` | `"vue-use-idb-keyval-4"` | const | `'vue-use-idb-keyval-4'` | ✗ |


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