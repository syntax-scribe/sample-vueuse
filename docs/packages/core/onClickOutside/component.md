[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/onClickOutside/component.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `RenderableComponent` | `../types` |
| `OnClickOutsideOptions` | `./index` |
| `onClickOutside` | `@vueuse/core` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `shallowRef` | `vue` |


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


---

## Interfaces

### `OnClickOutsideProps`

<details><summary>Interface Code</summary>

```ts
export interface OnClickOutsideProps extends RenderableComponent {
  options?: Omit<OnClickOutsideOptions, 'controls'>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `options` | `Omit<OnClickOutsideOptions, 'controls'>` | ✓ |  |


---

## Type Aliases

> No type aliases found in this file.


---