[⬅️ Back to Table of Contents](../../index.md)

# 📄 `_types.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 4 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/router/_types.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `RouteParamValueRaw` | `vue-router` |
| `useRoute` | `vue-router` |
| `useRouter` | `vue-router` |


---

## Interfaces

### `ReactiveRouteOptions`

<details><summary>Interface Code</summary>

```ts
export interface ReactiveRouteOptions {
  /**
   * Mode to update the router query, ref is also acceptable
   *
   * @default 'replace'
   */
  mode?: MaybeRef<'replace' | 'push'>

  /**
   * Route instance, use `useRoute()` if not given
   */
  route?: ReturnType<typeof useRoute>

  /**
   * Router instance, use `useRouter()` if not given
   */
  router?: ReturnType<typeof useRouter>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `mode` | `MaybeRef<'replace' | 'push'>` | ✓ |  |
| `route` | `ReturnType<typeof useRoute>` | ✓ |  |
| `router` | `ReturnType<typeof useRouter>` | ✓ |  |

### `ReactiveRouteOptionsWithTransform<V, R>`

<details><summary>Interface Code</summary>

```ts
export interface ReactiveRouteOptionsWithTransform<V, R> extends ReactiveRouteOptions {
  /**
   * Function to transform data before return, or an object with one or both functions:
   * `get` to transform data before returning, and `set` to transform data before setting
   */
  transform?:
    | ((val: V) => R)
    | ({
      get?: (value: V) => R
      set?: (value: R) => V
    })
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `transform` | `| ((val: V) => R)
    | ({
      get?: (value: V) => R
      set?: (value: R) => V
    })` | ✓ |  |


---

## Type Aliases

### `RouteQueryValueRaw`

```ts
type RouteQueryValueRaw = RouteParamValueRaw | string[];
```

### `RouteHashValueRaw`

```ts
type RouteHashValueRaw = string | null | undefined;
```


---