[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/math/useCeil/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useCeil(value: MaybeRefOrGetter<number>): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function useCeil(value: MaybeRefOrGetter<number>): ComputedRef<number> {
  return computed<number>(() => Math.ceil(toValue(value)))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Math.ceil`.
 *
 * @see https://vueuse.org/useCeil
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<number>`
- **Return Type**: `ComputedRef<number>`
- **Calls**:
  - `computed (from vue)`
  - `Math.ceil`
  - `toValue (from vue)`

---