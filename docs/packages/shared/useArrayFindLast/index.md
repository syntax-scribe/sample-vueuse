[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/useArrayFindLast/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `index` | `number` | let/var | `arr.length` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `findLast(arr: T[], cb: (element: T, index: number, array: T[]) => boolean): T | undefined`

<details><summary>Code</summary>

```ts
function findLast<T>(arr: T[], cb: (element: T, index: number, array: T[]) => boolean): T | undefined {
  let index = arr.length
  while (index-- > 0) {
    if (cb(arr[index], index, arr))
      return arr[index]
  }
  return undefined
}
```
</details>

- **Parameters**:
  - `arr: T[]`
  - `cb: (element: T, index: number, array: T[]) => boolean`
- **Return Type**: `T | undefined`
- **Calls**:
  - `cb`
### `useArrayFindLast(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => boolean): UseArrayFindLastReturn<T>`

<details><summary>Code</summary>

```ts
export function useArrayFindLast<T>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => boolean,
): UseArrayFindLastReturn<T> {
  return computed(() =>
    toValue<T | undefined>(
      !Array.prototype.findLast
        ? findLast(toValue(list), (element, index, array) => fn(toValue(element), index, array))
        : toValue(list)
            .findLast((element, index, array) => fn(toValue(element), index, array)),
    ))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.findLast`
 *
 * @see https://vueuse.org/useArrayFindLast
 * @param list - the array was called upon.
 * @param fn - a function to test each element.
 *
 * @returns the last element in the array that satisfies the provided testing function. Otherwise, undefined is returned.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => boolean`
- **Return Type**: `UseArrayFindLastReturn<T>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`
  - `findLast`
  - `fn`
  - `toValue(list)
            .findLast`

---

## Type Aliases

### `UseArrayFindLastReturn<T = any = any>`

```ts
type UseArrayFindLastReturn<T = any = any> = ComputedRef<T | undefined>;
```


---