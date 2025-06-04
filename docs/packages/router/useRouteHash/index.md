[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/router/useRouteHash/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ReactiveRouteOptions` | `../_types` |
| `RouteHashValueRaw` | `../_types` |
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
| `_hash` | `RouteHashValueRaw` | let/var | `*not shown*` | ✗ |
| `_trigger` | `() => void` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useRouteHash(defaultValue: MaybeRefOrGetter<RouteHashValueRaw>, {
    mode = 'replace',
    route = useRoute(),
    router = useRouter(),
  }: ReactiveRouteOptions): any`

<details><summary>Code</summary>

```ts
export function useRouteHash(
  defaultValue?: MaybeRefOrGetter<RouteHashValueRaw>,
  {
    mode = 'replace',
    route = useRoute(),
    router = useRouter(),
  }: ReactiveRouteOptions = {},
) {
  _hash = route.hash

  tryOnScopeDispose(() => {
    _hash = undefined
  })

  let _trigger: () => void

  const proxy = customRef<RouteHashValueRaw>((track, trigger) => {
    _trigger = trigger

    return {
      get() {
        track()

        return _hash || toValue(defaultValue)
      },
      set(v) {
        if (v === _hash)
          return

        _hash = v === null ? undefined : v

        trigger()

        nextTick(() => {
          const { params, query } = route

          router[toValue(mode)]({ params, query, hash: _hash as string })
        })
      },
    }
  })

  watch(
    () => route.hash,
    () => {
      if (route.hash === _hash)
        return

      _hash = route.hash
      _trigger()
    },
    { flush: 'sync' },
  )

  return proxy
}
```
</details>

- **Parameters**:
  - `defaultValue: MaybeRefOrGetter<RouteHashValueRaw>`
  - `{
    mode = 'replace',
    route = useRoute(),
    router = useRouter(),
  }: ReactiveRouteOptions`
- **Return Type**: `any`
- **Calls**:
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `customRef (from vue)`
  - `track`
  - `toValue (from vue)`
  - `trigger`
  - `nextTick (from vue)`
  - `complex_call_997`
  - `watch (from vue)`
  - `_trigger`

---