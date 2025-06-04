[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 13 |
| 📊 Variables & Constants | 4 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/router/useRouteParams/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `LocationAsRelativeRaw` | `vue-router` |
| `RouteParamValueRaw` | `vue-router` |
| `Router` | `vue-router` |
| `ReactiveRouteOptionsWithTransform` | `../_types` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `customRef` | `vue` |
| `nextTick` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `useRoute` | `vue-router` |
| `useRouter` | `vue-router` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `_queue` | `WeakMap<Router, Map<string, any>>` | const | `new WeakMap<Router, Map<string, any>>()` | ✗ |
| `_paramsQueue` | `Map<string, any>` | const | `_queue.get(router)!` | ✗ |
| `param` | `any` | let/var | `route.params[name] as any` | ✗ |
| `_trigger` | `() => void` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useRouteParams(name: string): Ref<null | string | string[]>`

<details><summary>Code</summary>

```ts
export function useRouteParams(
  name: string
): Ref<null | string | string[]>
```
</details>

- **Parameters**:
  - `name: string`
- **Return Type**: `Ref<null | string | string[]>`
### `transformGet(value: T): K`

<details><summary>Code</summary>

```ts
(value: T) => value as unknown as K
```
</details>

- **Parameters**:
  - `value: T`
- **Return Type**: `K`
### `transformSet(value: K): T`

<details><summary>Code</summary>

```ts
(value: K) => value as unknown as T
```
</details>

- **Parameters**:
  - `value: K`
- **Return Type**: `T`

---