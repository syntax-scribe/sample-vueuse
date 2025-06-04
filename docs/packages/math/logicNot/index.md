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
📂 **`packages/math/logicNot/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `logicNot(v: MaybeRefOrGetter<any>): ComputedRef<boolean>`

<details><summary>Code</summary>

```ts
export function logicNot(v: MaybeRefOrGetter<any>): ComputedRef<boolean> {
  return computed(() => !toValue(v))
}
```
</details>

- **JSDoc**:
```ts
/**
 * `NOT` conditions for refs.
 *
 * @see https://vueuse.org/logicNot
 */
```

- **Parameters**:
  - `v: MaybeRefOrGetter<any>`
- **Return Type**: `ComputedRef<boolean>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`

---