[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 4 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useElementSize/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `ElementSize` | `./index` |
| `watch` | `vue` |
| `useElementSize` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `handler` | `any` | const | `typeof binding.value === 'function' ? binding.value : binding.value?.[0]` | ✗ |
| `options` | `[initialSize?: ElementSize, options?: UseResizeObserverOptions]` | const | `(typeof binding.value === 'function' ? [] : binding.value.slice(1)) as RemoveFirstFromTuple<BindingValueArray>` | ✗ |
| `vElementSize` | `ObjectDirective<
  HTMLElement,
  BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    const handler = typeof binding.value === 'function' ? binding.value : binding.value?.[0]
    const options = (typeof binding.value === 'function' ? [] : binding.value.slice(1)) as RemoveFirstFromTuple<BindingValueArray>

    const { width, height } = useElementSize(el, ...options)
    watch([width, height], ([width, height]) => handler({ width, height }))
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
    const handler = typeof binding.value === 'function' ? binding.value : binding.value?.[0]
    const options = (typeof binding.value === 'function' ? [] : binding.value.slice(1)) as RemoveFirstFromTuple<BindingValueArray>

    const { width, height } = useElementSize(el, ...options)
    watch([width, height], ([width, height]) => handler({ width, height }))
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `binding.value.slice`
  - `useElementSize (from ./index)`
  - `watch (from vue)`
  - `handler`

---

## Type Aliases

### `RemoveFirstFromTuple<T extends any[] extends any[]>`

```ts
type RemoveFirstFromTuple<T extends any[] extends any[]> = T['length'] extends 0 ? undefined :
      (((...b: T) => void) extends (a: any, ...b: infer I) => void ? I : []);
```

### `BindingValueFunction`

```ts
type BindingValueFunction = (size: ElementSize) => void;
```

### `VElementSizeOptions`

```ts
type VElementSizeOptions = RemoveFirstFromTuple<Parameters<typeof useElementSize>>;
```

### `BindingValueArray`

```ts
type BindingValueArray = [BindingValueFunction, ...VElementSizeOptions];
```


---