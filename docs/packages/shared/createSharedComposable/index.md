[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/createSharedComposable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `EffectScope` | `vue` |
| `AnyFn` | `../utils` |
| `effectScope` | `vue` |
| `tryOnScopeDispose` | `../tryOnScopeDispose` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `subscribers` | `number` | let/var | `0` | ✗ |
| `state` | `ReturnType<Fn> | undefined` | let/var | `*not shown*` | ✗ |
| `scope` | `EffectScope | undefined` | let/var | `*not shown*` | ✗ |


---

## Functions

### `createSharedComposable(composable: Fn): SharedComposableReturn<Fn>`

<details><summary>Code</summary>

```ts
export function createSharedComposable<Fn extends AnyFn>(composable: Fn): SharedComposableReturn<Fn> {
  let subscribers = 0
  let state: ReturnType<Fn> | undefined
  let scope: EffectScope | undefined

  const dispose = () => {
    subscribers -= 1
    if (scope && subscribers <= 0) {
      scope.stop()
      state = undefined
      scope = undefined
    }
  }

  return <Fn>((...args) => {
    subscribers += 1
    if (!scope) {
      scope = effectScope(true)
      state = scope.run(() => composable(...args))
    }
    tryOnScopeDispose(dispose)
    return state
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Make a composable function usable with multiple Vue instances.
 *
 * @see https://vueuse.org/createSharedComposable
 */
```

- **Parameters**:
  - `composable: Fn`
- **Return Type**: `SharedComposableReturn<Fn>`
- **Calls**:
  - `scope.stop`
  - `effectScope (from vue)`
  - `scope.run`
  - `composable`
  - `tryOnScopeDispose (from ../tryOnScopeDispose)`
### `dispose(): void`

<details><summary>Code</summary>

```ts
() => {
    subscribers -= 1
    if (scope && subscribers <= 0) {
      scope.stop()
      state = undefined
      scope = undefined
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `scope.stop`

---

## Type Aliases

### `SharedComposableReturn<T extends AnyFn = AnyFn extends AnyFn = AnyFn>`

```ts
type SharedComposableReturn<T extends AnyFn = AnyFn extends AnyFn = AnyFn> = T;
```


---