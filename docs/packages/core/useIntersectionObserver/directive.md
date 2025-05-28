[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 1 |
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
📂 **`packages/core/useIntersectionObserver/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `UseIntersectionObserverOptions` | `./index` |
| `useIntersectionObserver` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `vIntersectionObserver` | `ObjectDirective<
  HTMLElement,
BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    if (typeof binding.value === 'function')
      useIntersectionObserver(el, binding.value)
    else
      useIntersectionObserver(el, ...binding.value)
  },
}` | ✓ |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    if (typeof binding.value === 'function')
      useIntersectionObserver(el, binding.value)
    else
      useIntersectionObserver(el, ...binding.value)
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `useIntersectionObserver (from ./index)`

---

## Type Aliases

### `BindingValueFunction`

```ts
type BindingValueFunction = IntersectionObserverCallback;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, UseIntersectionObserverOptions];
```


---