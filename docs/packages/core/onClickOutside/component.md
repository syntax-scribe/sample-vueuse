[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 6 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)

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