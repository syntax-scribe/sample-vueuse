[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 12 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/router/useRouteQuery/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `Router` | `vue-router` |
| `ReactiveRouteOptionsWithTransform` | `../_types` |
| `RouteQueryValueRaw` | `../_types` |
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
| `_queriesQueue` | `Map<string, any>` | const | `_queue.get(router)!` | ✗ |
| `query` | `any` | let/var | `route.query[name] as any` | ✗ |
| `_trigger` | `() => void` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useRouteQuery(name: string): Ref<undefined | null | string | string[]>`

<details><summary>Code</summary>

```ts
export function useRouteQuery(
  name: string
): Ref<undefined | null | string | string[]>
```
</details>

- **Parameters**:
  - `name: string`
- **Return Type**: `Ref<undefined | null | string | string[]>`
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