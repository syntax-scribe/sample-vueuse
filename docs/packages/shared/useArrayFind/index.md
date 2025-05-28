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
📂 **`packages/shared/useArrayFind/index.ts`**

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

### `useArrayFind(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => boolean): UseArrayFindReturn<T>`

<details><summary>Code</summary>

```ts
export function useArrayFind<T>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => boolean,
): UseArrayFindReturn<T> {
  return computed(() =>
    toValue<T | undefined>(
      toValue(list)
        .find((element, index, array) => fn(toValue(element), index, array)),
    ))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.find`
 *
 * @see https://vueuse.org/useArrayFind
 * @param list - the array was called upon.
 * @param fn - a function to test each element.
 *
 * @returns the first element in the array that satisfies the provided testing function. Otherwise, undefined is returned.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `fn: (element: T, index: number, array: MaybeRefOrGetter<T>[]) => boolean`
- **Return Type**: `UseArrayFindReturn<T>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`
  - `toValue(list)
        .find`
  - `fn`

---

## Type Aliases

### `UseArrayFindReturn<T = any = any>`

```ts
type UseArrayFindReturn<T = any = any> = ComputedRef<T | undefined>;
```


---