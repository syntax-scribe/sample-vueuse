[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/math/useAverage/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `MaybeComputedRefArgs` | `../utils` |
| `computed` | `vue` |
| `toValueArgsFlat` | `../utils` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useAverage(array: MaybeRefOrGetter<MaybeRefOrGetter<number>[]>): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function useAverage(array: MaybeRefOrGetter<MaybeRefOrGetter<number>[]>): ComputedRef<number>
```
</details>

- **Parameters**:
  - `array: MaybeRefOrGetter<MaybeRefOrGetter<number>[]>`
- **Return Type**: `ComputedRef<number>`

---