[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useScrollLock/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `FunctionDirective` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `useScrollLock` | `./index` |


---

## Functions

### `onScrollLock(): FunctionDirective<
  HTMLElement,
  boolean
>`

<details><summary>Code</summary>

```ts
function onScrollLock(): FunctionDirective<
  HTMLElement,
  boolean
> {
  let isMounted = false
  const state = shallowRef(false)
  return (el, binding) => {
    state.value = binding.value
    if (isMounted)
      return
    isMounted = true
    const isLocked = useScrollLock(el, binding.value)
    watch(state, v => isLocked.value = v)
  }
}
```
</details>

- **Return Type**: `FunctionDirective<
  HTMLElement,
  boolean
>`
- **Calls**:
  - `shallowRef (from vue)`
  - `useScrollLock (from ./index)`
  - `watch (from vue)`

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