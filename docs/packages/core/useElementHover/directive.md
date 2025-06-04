[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 2 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useElementHover/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `UseElementHoverOptions` | `./index` |
| `watch` | `vue` |
| `useElementHover` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `value` | `any` | const | `binding.value` | ✗ |
| `vElementHover` | `ObjectDirective<
  HTMLElement,
  BindingValueFunction | [handler: BindingValueFunction, options: UseElementHoverOptions]
>` | const | `{
  mounted(el, binding) {
    const value = binding.value
    if (typeof value === 'function') {
      const isHovered = useElementHover(el)
      watch(isHovered, v => value(v))
    }
    else {
      const [handler, options] = value
      const isHovered = useElementHover(el, options)
      watch(isHovered, v => handler(v))
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
    const value = binding.value
    if (typeof value === 'function') {
      const isHovered = useElementHover(el)
      watch(isHovered, v => value(v))
    }
    else {
      const [handler, options] = value
      const isHovered = useElementHover(el, options)
      watch(isHovered, v => handler(v))
    }
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `useElementHover (from ./index)`
  - `watch (from vue)`
  - `value`
  - `handler`

---

## Type Aliases

### `BindingValueFunction`

```ts
type BindingValueFunction = (state: boolean) => void;
```


---