[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 9 |
| 📦 Imports | 14 |
| 📊 Variables & Constants | 20 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useFetch/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `AfterFetchContext` | `./index` |
| `OnFetchErrorContext` | `./index` |
| `until` | `@vueuse/shared` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `isBelowNode18` | `../../.test` |
| `createFetch` | `./index` |
| `useFetch` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `jsonMessage` | `{ hello: string; }` | const | `{ hello: 'world' }` | ✗ |
| `jsonUrl` | `string` | const | ``https://example.com?json=${encodeURI(JSON.stringify(jsonMessage))}`` | ✗ |
| `myHeaders` | `Headers` | let/var | `new Headers()` | ✗ |
| `count` | `number` | let/var | `0` | ✗ |
| `options` | `any` | let/var | `*not shown*` | ✗ |
| `options` | `any` | let/var | `*not shown*` | ✗ |
| `payload` | `number[]` | let/var | `[1, 2]` | ✗ |
| `options` | `{ immediate: boolean; }` | let/var | `{ immediate: false }` | ✗ |
| `error1` | `any` | let/var | `await useFetch('https://example.com?status=400', options).execute(true).catch(err => err)` | ✗ |
| `error2` | `any` | let/var | `await useFetch('https://example.com?status=600', options).execute(true).catch(err => err)` | ✗ |
| `baseUrl` | `"https://example.com"` | let/var | `'https://example.com'` | ✗ |
| `targetUrl` | `"https://example.com/test"` | let/var | ``${baseUrl}/test`` | ✗ |
| `fetchHeaders` | `{ Authorization: string; }` | let/var | `{ Authorization: 'test' }` | ✗ |
| `requestHeaders` | `{ 'Accept-Language': string; }` | let/var | `{ 'Accept-Language': 'en-US' }` | ✗ |
| `allHeaders` | `{ 'Accept-Language': string; Authorization: string; }` | let/var | `{ ...fetchHeaders, ...requestHeaders }` | ✗ |
| `requestOptions` | `{ headers: { 'Accept-Language': string; }; }` | let/var | `{ headers: requestHeaders }` | ✗ |
| `count` | `number` | let/var | `0` | ✗ |
| `options` | `Partial<AfterFetchContext>` | let/var | `{}` | ✗ |
| `count` | `number` | let/var | `0` | ✗ |
| `options` | `Partial<OnFetchErrorContext>` | let/var | `{}` | ✗ |


---

## Functions

### `fetchSpyHeaders(idx: number): any`

<details><summary>Code</summary>

```ts
function fetchSpyHeaders(idx = 0) {
  return (fetchSpy.mock.calls[idx][1]! as any).headers
}
```
</details>

- **Parameters**:
  - `idx: number`
- **Return Type**: `any`
### `beforeFetch(ctx: BeforeFetchContext): void`

<details><summary>Code</summary>

```ts
(ctx) => {
        options = ctx.options
      }
```
</details>

- **Parameters**:
  - `ctx: BeforeFetchContext`
- **Return Type**: `void`
### `beforeFetch(ctx: BeforeFetchContext): void`

<details><summary>Code</summary>

```ts
(ctx) => {
        options = ctx.options
      }
```
</details>

- **Parameters**:
  - `ctx: BeforeFetchContext`
- **Return Type**: `void`
### `beforeFetch(ctx: BeforeFetchContext): void`

<details><summary>Code</summary>

```ts
(ctx) => {
        options = ctx.options
      }
```
</details>

- **Parameters**:
  - `ctx: BeforeFetchContext`
- **Return Type**: `void`
### `beforeFetch(ctx: BeforeFetchContext): void`

<details><summary>Code</summary>

```ts
(ctx) => {
        options = ctx.options
      }
```
</details>

- **Parameters**:
  - `ctx: BeforeFetchContext`
- **Return Type**: `void`
### `afterFetch(ctx: AfterFetchContext<any>): AfterFetchContext<any>`

<details><summary>Code</summary>

```ts
(ctx) => {
        !count && ctx.execute()
        count++
        options = ctx
        return ctx
      }
```
</details>

- **Parameters**:
  - `ctx: AfterFetchContext<any>`
- **Return Type**: `AfterFetchContext<any>`
- **Calls**:
  - `ctx.execute`
### `afterFetch(ctx: AfterFetchContext<any>): AfterFetchContext<any>`

<details><summary>Code</summary>

```ts
(ctx) => {
        !count && ctx.execute()
        count++
        options = ctx
        return ctx
      }
```
</details>

- **Parameters**:
  - `ctx: AfterFetchContext<any>`
- **Return Type**: `AfterFetchContext<any>`
- **Calls**:
  - `ctx.execute`
### `onFetchError(ctx: OnFetchErrorContext<any, any>): OnFetchErrorContext<any, any>`

<details><summary>Code</summary>

```ts
(ctx) => {
        !count && ctx.execute()
        count++
        options = ctx
        return ctx
      }
```
</details>

- **Parameters**:
  - `ctx: OnFetchErrorContext<any, any>`
- **Return Type**: `OnFetchErrorContext<any, any>`
- **Calls**:
  - `ctx.execute`
### `onFetchError(ctx: OnFetchErrorContext<any, any>): OnFetchErrorContext<any, any>`

<details><summary>Code</summary>

```ts
(ctx) => {
        !count && ctx.execute()
        count++
        options = ctx
        return ctx
      }
```
</details>

- **Parameters**:
  - `ctx: OnFetchErrorContext<any, any>`
- **Return Type**: `OnFetchErrorContext<any, any>`
- **Calls**:
  - `ctx.execute`

---