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
📂 **`packages/core/useScroll/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `UseScrollOptions` | `./index` |
| `UseScrollReturn` | `./index` |
| `useScroll` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `handler` | `any` | const | `binding.value` | ✗ |
| `vScroll` | `ObjectDirective<
  HTMLElement,
BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    if (typeof binding.value === 'function') {
      const handler = binding.value
      const state = useScroll(el, {
        onScroll() {
          handler(state)
        },
        onStop() {
          handler(state)
        },
      })
    }
    else {
      const [handler, options] = binding.value
      const state = useScroll(el, {
        ...options,
        onScroll(e) {
          options.onScroll?.(e)
          handler(state)
        },
        onStop(e) {
          options.onStop?.(e)
          handler(state)
        },
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
    if (typeof binding.value === 'function') {
      const handler = binding.value
      const state = useScroll(el, {
        onScroll() {
          handler(state)
        },
        onStop() {
          handler(state)
        },
      })
    }
    else {
      const [handler, options] = binding.value
      const state = useScroll(el, {
        ...options,
        onScroll(e) {
          options.onScroll?.(e)
          handler(state)
        },
        onStop(e) {
          options.onStop?.(e)
          handler(state)
        },
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
  - `useScroll (from ./index)`
  - `handler`
  - `options.onScroll`
  - `options.onStop`

---

## Type Aliases

### `BindingValueFunction`

```ts
type BindingValueFunction = (state: UseScrollReturn) => void;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, UseScrollOptions];
```


---