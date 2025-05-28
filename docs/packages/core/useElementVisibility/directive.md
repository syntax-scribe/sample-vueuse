[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useElementVisibility/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `UseElementVisibilityOptions` | `./index` |
| `watch` | `vue` |
| `useElementVisibility` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `handler` | `any` | const | `binding.value` | ✗ |
| `vElementVisibility` | `ObjectDirective<
  HTMLElement,
  BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    if (typeof binding.value === 'function') {
      const handler = binding.value
      const isVisible = useElementVisibility(el)
      watch(isVisible, v => handler(v), { immediate: true })
    }
    else {
      const [handler, options] = binding.value
      const isVisible = useElementVisibility(el, options)
      watch(isVisible, v => handler(v), { immediate: true })
    }
  },
}` | ✓ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    if (typeof binding.value === 'function') {
      const handler = binding.value
      const isVisible = useElementVisibility(el)
      watch(isVisible, v => handler(v), { immediate: true })
    }
    else {
      const [handler, options] = binding.value
      const isVisible = useElementVisibility(el, options)
      watch(isVisible, v => handler(v), { immediate: true })
    }
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `useElementVisibility (from ./index)`
  - `watch (from vue)`
  - `handler`

---

## Type Aliases

### `BindingValueFunction`

```ts
type BindingValueFunction = (state: boolean) => void;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, UseElementVisibilityOptions];
```


---