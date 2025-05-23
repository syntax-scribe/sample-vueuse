[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/onKeyStroke/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `OnKeyStrokeOptions` | `./index` |
| `onKeyStroke` | `./index` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


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