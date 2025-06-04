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
📂 **`packages/shared/useToString/index.ts`**

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

### `useToString(value: MaybeRefOrGetter<unknown>): ComputedRef<string>`

<details><summary>Code</summary>

```ts
export function useToString(
  value: MaybeRefOrGetter<unknown>,
): ComputedRef<string> {
  return computed(() => `${toValue(value)}`)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively convert a ref to string.
 *
 * @see https://vueuse.org/useToString
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<unknown>`
- **Return Type**: `ComputedRef<string>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`

---