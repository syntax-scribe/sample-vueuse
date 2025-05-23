[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useArrayReduce/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `useArrayReduce(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, reducer: UseArrayReducer<T, T, T>): ComputedRef<T>`

<details><summary>Code</summary>

```ts
export function useArrayReduce<T>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  reducer: UseArrayReducer<T, T, T>,
): ComputedRef<T>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.reduce`
 *
 * @see https://vueuse.org/useArrayReduce
 * @param list - the array was called upon.
 * @param reducer - a "reducer" function.
 *
 * @returns the value that results from running the "reducer" callback function to completion over the entire array.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `reducer: UseArrayReducer<T, T, T>`
- **Return Type**: `ComputedRef<T>`
### `reduceCallback(sum: any, value: any, index: number): any`

<details><summary>Code</summary>

```ts
(sum: any, value: any, index: number) => reducer(toValue(sum), toValue(value), index)
```
</details>

- **Parameters**:
  - `sum: any`
  - `value: any`
  - `index: number`
- **Return Type**: `any`
- **Calls**:
  - `reducer`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseArrayReducer<PV, CV, R>`

```ts
type UseArrayReducer<PV, CV, R> = (previousValue: PV, currentValue: CV, currentIndex: number) => R;
```


---