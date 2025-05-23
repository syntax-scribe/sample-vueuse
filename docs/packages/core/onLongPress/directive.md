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
📂 **`packages/core/onLongPress/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `OnLongPressOptions` | `./index` |
| `onLongPress` | `./index` |


---

## Functions

### `mounted(el: any, binding: any): void`

<details><summary>Code</summary>

```ts
mounted(el, binding) {
    if (typeof binding.value === 'function')
      onLongPress(el, binding.value, { modifiers: binding.modifiers })
    else
      onLongPress(el, ...binding.value)
  }
```
</details>

- **Parameters**:
  - `el: any`
  - `binding: any`
- **Return Type**: `void`
- **Calls**:
  - `onLongPress (from ./index)`

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
type BindingValueFunction = (evt: PointerEvent) => void;
```

### `BindingValueArray`

```ts
type BindingValueArray = [
  BindingValueFunction,
  OnLongPressOptions,
];
```


---