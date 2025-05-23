[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 13
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---