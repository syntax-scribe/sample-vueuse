[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/useArrayFindIndex/index.ts`**

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

### `useArrayFindIndex(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => unknown): UseArrayFindIndexReturn`

<details><summary>Code</summary>

```ts
export function useArrayFindIndex<T>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => unknown,
): UseArrayFindIndexReturn {
  return computed(() => toValue(list).findIndex((element, index, array) => fn(toValue(element), index, array)))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.findIndex`
 *
 * @see https://vueuse.org/useArrayFindIndex
 * @param list - the array was called upon.
 * @param fn - a function to test each element.
 *
 * @returns the index of the first element in the array that passes the test. Otherwise, "-1".
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => unknown`
- **Return Type**: `UseArrayFindIndexReturn`
- **Calls**:
  - `computed (from vue)`
  - `toValue(list).findIndex`
  - `fn`
  - `toValue (from vue)`

---

## Type Aliases

### `UseArrayFindIndexReturn`

```ts
type UseArrayFindIndexReturn = ComputedRef<number>;
```


---