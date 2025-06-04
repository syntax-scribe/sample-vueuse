[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 13 |
| 📊 Variables & Constants | 15 |
| 📐 Interfaces | 4 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/integrations/useAxios/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `RawAxiosRequestConfig` | `axios` |
| `UseAxiosOptions` | `./index` |
| `UseAxiosOptionsBase` | `./index` |
| `UseAxiosOptionsWithInitialData` | `./index` |
| `axios` | `axios` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `expectTypeOf` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `isBelowNode18` | `../../.test` |
| `useAxios` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `url` | `"https://jsonplaceholder.typicode.com/todos/1"` | const | `'https://jsonplaceholder.typicode.com/todos/1'` | ✗ |
| `config` | `RawAxiosRequestConfig` | const | `{
    method: 'GET',
  }` | ✗ |
| `options` | `{ immediate: boolean; }` | const | `{ immediate: false }` | ✗ |
| `path` | `"/todos/1"` | const | `'/todos/1'` | ✗ |
| `result` | `StrictUseAxiosReturn<any, AxiosResponse<T>, any, UseAxiosOptionsWithInitialData<any>>` | let/var | `await then(undefined, onRejected)` | ✗ |
| `result` | `EasyUseAxiosReturn<any, AxiosResponse<T>, any>` | let/var | `await then(undefined, onRejected)` | ✗ |
| `result` | `EasyUseAxiosReturn<any, AxiosResponse<T>, any>` | let/var | `await res.then(undefined, onRejected)` | ✗ |
| `paramConfig` | `RawAxiosRequestConfig` | let/var | `{ params: { postId: 1 } }` | ✗ |
| `typeConfig` | `RawAxiosRequestConfig<ReqType>` | let/var | `{
      method: 'POST',
    }` | ✗ |
| `requestData` | `ReqType` | let/var | `{
      title: 'title',
      body: 'body',
      userId: 123,
    }` | ✗ |
| `error` | `any` | let/var | `*not shown*` | ✗ |
| `error` | `any` | let/var | `*not shown*` | ✗ |
| `initialData` | `ResType` | let/var | `{
      id: 2,
      title: 'title',
      body: 'body',
      userId: 2,
    }` | ✗ |
| `initialData` | `ResType` | let/var | `{
      id: 2,
      title: 'title',
      body: 'body',
      userId: 2,
    }` | ✗ |
| `o` | `UseAxiosOptions<number>` | let/var | `{ ...options, initialData: 1 }` | ✗ |


---

## Interfaces

### `ReqType`

<details><summary>Interface Code</summary>

```ts
interface ReqType {
      title: string
      body: string
      userId: number
    }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `title` | `string` | ✗ |  |
| `body` | `string` | ✗ |  |
| `userId` | `number` | ✗ |  |

### `ResType`

<details><summary>Interface Code</summary>

```ts
interface ResType {
      id: number
      title: string
      body: string
      userId: number
    }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `id` | `number` | ✗ |  |
| `title` | `string` | ✗ |  |
| `body` | `string` | ✗ |  |
| `userId` | `number` | ✗ |  |

### `ResType`

<details><summary>Interface Code</summary>

```ts
interface ResType {
      id: number
      title: string
      body: string
      userId: number
    }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `id` | `number` | ✗ |  |
| `title` | `string` | ✗ |  |
| `body` | `string` | ✗ |  |
| `userId` | `number` | ✗ |  |

### `ResType`

<details><summary>Interface Code</summary>

```ts
interface ResType {
      id: number
      title: string
      body: string
      userId: number
    }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `id` | `number` | ✗ |  |
| `title` | `string` | ✗ |  |
| `body` | `string` | ✗ |  |
| `userId` | `number` | ✗ |  |


---