[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useElementBounding/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `UseElementBoundingOptions` | `./index` |
| `UseElementBoundingReturn` | `./index` |
| `watch` | `vue` |
| `useElementBounding` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `vElementBounding` | `ObjectDirective<
  HTMLElement,
  BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    const [handler, options] = (typeof binding.value === 'function' ? [binding.value, {}] : binding.value) as BindingValueArray

    const {
      height,
      bottom,
      left,
      right,
      top,
      width,
      x,
      y,
    } = useElementBounding(el, options)
    watch([height, bottom, left, right, top, width, x, y], () => handler({ height, bottom, left, right, top, width, x, y }))
  },
}` | ✓ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    const [handler, options] = (typeof binding.value === 'function' ? [binding.value, {}] : binding.value) as BindingValueArray

    const {
      height,
      bottom,
      left,
      right,
      top,
      width,
      x,
      y,
    } = useElementBounding(el, options)
    watch([height, bottom, left, right, top, width, x, y], () => handler({ height, bottom, left, right, top, width, x, y }))
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `useElementBounding (from ./index)`
  - `watch (from vue)`
  - `handler`

---

## Type Aliases

### `ElementBounding`

```ts
type ElementBounding = Omit<UseElementBoundingReturn, 'update'>;
```

### `BindingValueFunction`

```ts
type BindingValueFunction = (bounding: ElementBounding) => void;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, UseElementBoundingOptions];
```


---