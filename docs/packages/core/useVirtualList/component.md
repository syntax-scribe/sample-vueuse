[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 5 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useVirtualList/component.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseVirtualListOptions` | `@vueuse/core` |
| `useVirtualList` | `@vueuse/core` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `toRefs` | `vue` |


---

## Interfaces

### `UseVirtualListProps`

<details><summary>Interface Code</summary>

```ts
export interface UseVirtualListProps {
  /**
   * data of scrollable list
   *
   * @default []
   */
  list: Array<any>
  /**
   * useVirtualList's options
   *
   * @default {}
   */
  options: UseVirtualListOptions
  /**
   * virtualList's height
   *
   * @default 300px
   */
  height: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `list` | `Array<any>` | ✗ |  |
| `options` | `UseVirtualListOptions` | ✗ |  |
| `height` | `string` | ✗ |  |


---