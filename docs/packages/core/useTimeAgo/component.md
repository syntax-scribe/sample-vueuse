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
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useTimeAgo/component.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseTimeAgoOptions` | `@vueuse/core` |
| `MaybeRef` | `vue` |
| `useTimeAgo` | `@vueuse/core` |
| `defineComponent` | `vue` |
| `reactive` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |


---

## 🔧 Functions

> No functions found in this file.


---

## Interfaces

### `UseTimeAgoComponentOptions`

<details><summary>Interface Code</summary>

```ts
interface UseTimeAgoComponentOptions extends Omit<UseTimeAgoOptions<true>, 'controls'> {
  time: MaybeRef<Date | number | string>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `time` | `MaybeRef<Date | number | string>` | ✗ |  |


---