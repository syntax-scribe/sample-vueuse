[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |
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
📂 **`packages/core/useScrollLock/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `FunctionDirective` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `useScrollLock` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `isMounted` | `boolean` | let/var | `false` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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