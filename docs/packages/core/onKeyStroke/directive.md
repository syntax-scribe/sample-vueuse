[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/onKeyStroke/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `OnKeyStrokeOptions` | `./index` |
| `onKeyStroke` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `keys` | `any` | const | `binding.arg?.split(',') ?? true` | ✗ |
| `vOnKeyStroke` | `ObjectDirective<
  HTMLElement,
  BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    const keys = binding.arg?.split(',') ?? true
    if (typeof binding.value === 'function') {
      onKeyStroke(keys, binding.value, {
        target: el,
      })
    }
    else {
      const [handler, options] = binding.value
      onKeyStroke(keys, handler, {
        target: el,
        ...options,
      })
    }
  },
}` | ✓ |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    const keys = binding.arg?.split(',') ?? true
    if (typeof binding.value === 'function') {
      onKeyStroke(keys, binding.value, {
        target: el,
      })
    }
    else {
      const [handler, options] = binding.value
      onKeyStroke(keys, handler, {
        target: el,
        ...options,
      })
    }
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `binding.arg?.split`
  - `onKeyStroke (from ./index)`

---

## Type Aliases

### `BindingValueFunction`

```ts
type BindingValueFunction = (event: KeyboardEvent) => void;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, OnKeyStrokeOptions];
```


---