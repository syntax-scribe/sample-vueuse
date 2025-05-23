[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/createGlobalState/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `AnyFn` | `../utils` |
| `effectScope` | `vue` |


---

## Functions

### `createGlobalState(stateFactory: Fn): CreateGlobalStateReturn<Fn>`

<details><summary>Code</summary>

```ts
export function createGlobalState<Fn extends AnyFn>(
  stateFactory: Fn,
): CreateGlobalStateReturn<Fn> {
  let initialized = false
  let state: any
  const scope = effectScope(true)

  return ((...args: any[]) => {
    if (!initialized) {
      state = scope.run(() => stateFactory(...args))!
      initialized = true
    }
    return state
  }) as Fn
}
```
</details>

- **JSDoc**:
```ts
/**
 * Keep states in the global scope to be reusable across Vue instances.
 *
 * @see https://vueuse.org/createGlobalState
 * @param stateFactory A factory function to create the state
 */
```

- **Parameters**:
  - `stateFactory: Fn`
- **Return Type**: `CreateGlobalStateReturn<Fn>`
- **Calls**:
  - `effectScope (from vue)`
  - `scope.run`
  - `stateFactory`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `CreateGlobalStateReturn<Fn extends AnyFn = AnyFn extends AnyFn = AnyFn>`

```ts
type CreateGlobalStateReturn<Fn extends AnyFn = AnyFn extends AnyFn = AnyFn> = Fn;
```


---