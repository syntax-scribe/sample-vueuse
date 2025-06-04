[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 4 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


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

## Type Aliases

### `UseArrayReducer<PV, CV, R>`

```ts
type UseArrayReducer<PV, CV, R> = (previousValue: PV, currentValue: CV, currentIndex: number) => R;
```


---