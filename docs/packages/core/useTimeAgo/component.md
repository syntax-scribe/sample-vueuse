[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 5 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |

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