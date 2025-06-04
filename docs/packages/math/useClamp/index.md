[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 9 |
| 🟢 Vue Composition API | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/math/useClamp/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ReadonlyRefOrGetter` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `clamp` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `isReadonly` | `vue` |
| `toValue` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useClamp(value: ReadonlyRefOrGetter<number>, min: MaybeRefOrGetter<number>, max: MaybeRefOrGetter<number>): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function useClamp(
  value: ReadonlyRefOrGetter<number>,
  min: MaybeRefOrGetter<number>,
  max: MaybeRefOrGetter<number>,
): ComputedRef<number>
```
</details>

- **Parameters**:
  - `value: ReadonlyRefOrGetter<number>`
  - `min: MaybeRefOrGetter<number>`
  - `max: MaybeRefOrGetter<number>`
- **Return Type**: `ComputedRef<number>`

---