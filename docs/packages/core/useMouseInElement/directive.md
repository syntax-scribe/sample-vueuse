[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 3 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useMouseInElement/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `Reactive` | `vue` |
| `MouseInElementOptions` | `./index` |
| `UseMouseInElementReturn` | `./index` |
| `reactiveOmit` | `@vueuse/shared` |
| `reactive` | `vue` |
| `watch` | `vue` |
| `useMouseInElement` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `vMouseInElement` | `ObjectDirective<
  HTMLElement,
  BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    const [handler, options] = (typeof binding.value === 'function' ? [binding.value, {}] : binding.value) as BindingValueArray

    const state = reactiveOmit(reactive(useMouseInElement(el, options)), 'stop')
    watch(state, val => handler(val))
  },
}` | ✓ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    const [handler, options] = (typeof binding.value === 'function' ? [binding.value, {}] : binding.value) as BindingValueArray

    const state = reactiveOmit(reactive(useMouseInElement(el, options)), 'stop')
    watch(state, val => handler(val))
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `reactiveOmit (from @vueuse/shared)`
  - `reactive (from vue)`
  - `useMouseInElement (from ./index)`
  - `watch (from vue)`
  - `handler`

---

## Type Aliases

### `MouseInElement`

```ts
type MouseInElement = Omit<UseMouseInElementReturn, 'stop'>;
```

### `BindingValueFunction`

```ts
type BindingValueFunction = (mouse: Reactive<MouseInElement>) => void;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, MouseInElementOptions];
```


---