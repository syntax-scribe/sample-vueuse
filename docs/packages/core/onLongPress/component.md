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
📂 **`packages/core/onLongPress/component.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `RenderableComponent` | `../types` |
| `OnLongPressOptions` | `./index` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `shallowRef` | `vue` |
| `onLongPress` | `./index` |


---

## Interfaces

### `OnLongPressProps`

<details><summary>Interface Code</summary>

```ts
export interface OnLongPressProps extends RenderableComponent {
  options?: OnLongPressOptions
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `options` | `OnLongPressOptions` | ✓ |  |


---