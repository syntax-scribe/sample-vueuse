[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/useArraySome/index.ts`**

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

### `useArraySome(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => unknown): UseArraySomeReturn`

<details><summary>Code</summary>

```ts
export function useArraySome<T>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => unknown,
): UseArraySomeReturn {
  return computed(() => toValue(list).some((element, index, array) => fn(toValue(element), index, array)))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.some`
 *
 * @see https://vueuse.org/useArraySome
 * @param list - the array was called upon.
 * @param fn - a function to test each element.
 *
 * @returns **true** if the `fn` function returns a **truthy** value for any element from the array. Otherwise, **false**.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => unknown`
- **Return Type**: `UseArraySomeReturn`
- **Calls**:
  - `computed (from vue)`
  - `toValue(list).some`
  - `fn`
  - `toValue (from vue)`

---

## Type Aliases

### `UseArraySomeReturn`

```ts
type UseArraySomeReturn = ComputedRef<boolean>;
```


---