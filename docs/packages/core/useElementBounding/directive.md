[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 3

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


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