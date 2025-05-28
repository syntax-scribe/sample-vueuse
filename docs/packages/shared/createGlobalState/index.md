[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/createGlobalState/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `AnyFn` | `../utils` |
| `effectScope` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `initialized` | `boolean` | let/var | `false` | ✗ |
| `state` | `any` | let/var | `*not shown*` | ✗ |


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

## Type Aliases

### `CreateGlobalStateReturn<Fn extends AnyFn = AnyFn extends AnyFn = AnyFn>`

```ts
type CreateGlobalStateReturn<Fn extends AnyFn = AnyFn extends AnyFn = AnyFn> = Fn;
```


---