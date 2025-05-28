[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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

## 🔧 Functions

> No functions found in this file.


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