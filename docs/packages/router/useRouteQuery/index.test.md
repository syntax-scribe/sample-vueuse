[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 105 |
| 🧱 Classes | 0 |
| 📦 Imports | 14 |
| 📊 Variables & Constants | 20 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 5 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/router/useRouteQuery/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `effectScope` | `vue` |
| `nextTick` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `useRouteQuery` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `router` | `any` | const | `{} as any` | ✗ |
| `transform` | `NumberConstructor` | const | `Number` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | const | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | const | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `defaultPage` | `"DEFAULT_PAGE"` | let/var | `'DEFAULT_PAGE'` | ✗ |
| `router` | `any` | const | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | const | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => Object.assign(route, r) } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => {
      Object.keys(r.query).forEach(queryKey => r.query[queryKey] = String(r.query[queryKey]))
      return Object.assign(route, r)
    } } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | const | `{ replace: (r: any) => route = r } as any` | ✗ |
| `router` | `any` | let/var | `{ replace: (r: any) => route = r } as any` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `getRoute(query: Record<string, any>): any`

<details><summary>Code</summary>

```ts
(query: Record<string, any> = {}) => reactive({
    query,
    fullPath: '',
    hash: '',
    matched: [],
    meta: {},
    name: '',
    params: {},
    path: '',
    redirectedFrom: undefined,
  })
```
</details>

- **Parameters**:
  - `query: Record<string, any>`
- **Return Type**: `any`
- **Calls**:
  - `reactive (from vue)`
### `toArray(param: string | string[] | null): string[]`

<details><summary>Code</summary>

```ts
(param: string | string[] | null) => Array.isArray(param) ? param : [param]
```
</details>

- **Parameters**:
  - `param: string | string[] | null`
- **Return Type**: `string[]`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `get(value: string): any`

<details><summary>Code</summary>

```ts
(value: string) => JSON.parse(value)
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `set(value: any): string`

<details><summary>Code</summary>

```ts
(value: any) => JSON.stringify(value)
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `get(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `set(value: string): string`

<details><summary>Code</summary>

```ts
(value: string) => value.toLowerCase()
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `string`
- **Calls**:
  - `value.toLowerCase`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => Object.assign(route, r)
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => Object.assign(route, r)
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => Object.assign(route, r)
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => Object.assign(route, r)
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => {
      Object.keys(r.query).forEach(queryKey => r.query[queryKey] = String(r.query[queryKey]))
      return Object.assign(route, r)
    }
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.keys(r.query).forEach`
  - `String`
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => {
      Object.keys(r.query).forEach(queryKey => r.query[queryKey] = String(r.query[queryKey]))
      return Object.assign(route, r)
    }
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.keys(r.query).forEach`
  - `String`
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => {
      Object.keys(r.query).forEach(queryKey => r.query[queryKey] = String(r.query[queryKey]))
      return Object.assign(route, r)
    }
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.keys(r.query).forEach`
  - `String`
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => {
      Object.keys(r.query).forEach(queryKey => r.query[queryKey] = String(r.query[queryKey]))
      return Object.assign(route, r)
    }
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
- **Calls**:
  - `Object.keys(r.query).forEach`
  - `String`
  - `Object.assign`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `defaultLang(): string`

<details><summary>Code</summary>

```ts
() => 'pt-BR'
```
</details>

- **Return Type**: `string`
### `value(): string`

<details><summary>Code</summary>

```ts
() => 'default'
```
</details>

- **Return Type**: `string`
### `value(): string`

<details><summary>Code</summary>

```ts
() => 'default'
```
</details>

- **Return Type**: `string`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`
### `replace(r: any): any`

<details><summary>Code</summary>

```ts
(r: any) => route = r
```
</details>

- **Parameters**:
  - `r: any`
- **Return Type**: `any`

---