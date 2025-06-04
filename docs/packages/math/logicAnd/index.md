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
📂 **`packages/math/logicAnd/index.ts`**

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

### `logicAnd(args: MaybeRefOrGetter<any>[]): ComputedRef<boolean>`

<details><summary>Code</summary>

```ts
export function logicAnd(...args: MaybeRefOrGetter<any>[]): ComputedRef<boolean> {
  return computed(() => args.every(i => toValue(i)))
}
```
</details>

- **JSDoc**:
```ts
/**
 * `AND` conditions for refs.
 *
 * @see https://vueuse.org/logicAnd
 */
```

- **Parameters**:
  - `args: MaybeRefOrGetter<any>[]`
- **Return Type**: `ComputedRef<boolean>`
- **Calls**:
  - `computed (from vue)`
  - `args.every`
  - `toValue (from vue)`

---