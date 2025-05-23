[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `SharedComposableReturn<T extends AnyFn = AnyFn extends AnyFn = AnyFn>`

```ts
type SharedComposableReturn<T extends AnyFn = AnyFn extends AnyFn = AnyFn> = T;
```


---