[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 0
- **Type Aliases**: 3

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


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