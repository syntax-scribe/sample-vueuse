[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseArrayFindReturn<T = any = any>`

```ts
type UseArrayFindReturn<T = any = any> = ComputedRef<T | undefined>;
```


---