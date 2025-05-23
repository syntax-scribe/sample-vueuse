[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 9
- **Classes**: 0
- **Imports**: 14
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---