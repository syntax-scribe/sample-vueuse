[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `directive.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 1 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/onLongPress/directive.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ObjectDirective` | `vue` |
| `OnLongPressOptions` | `./index` |
| `onLongPress` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `vOnLongPress` | `ObjectDirective<
  HTMLElement,
  BindingValueFunction | BindingValueArray
>` | const | `{
  mounted(el, binding) {
    if (typeof binding.value === 'function')
      onLongPress(el, binding.value, { modifiers: binding.modifiers })
    else
      onLongPress(el, ...binding.value)
  },
}` | ✓ |


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