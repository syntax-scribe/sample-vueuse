[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
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