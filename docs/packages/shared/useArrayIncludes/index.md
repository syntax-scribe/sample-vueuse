[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/shared/useArrayIncludes/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |
| `containsProp` | `../utils` |
| `isObject` | `../utils` |


---

## Functions

### `isArrayIncludesOptions(obj: any): obj is UseArrayIncludesOptions<T, V>`

<details><summary>Code</summary>

```ts
function isArrayIncludesOptions<T, V>(obj: any): obj is UseArrayIncludesOptions<T, V> {
  return isObject(obj) && containsProp(obj, 'formIndex', 'comparator')
}
```
</details>

- **Parameters**:
  - `obj: any`
- **Return Type**: `obj is UseArrayIncludesOptions<T, V>`
- **Calls**:
  - `isObject (from ../utils)`
  - `containsProp (from ../utils)`
### `useArrayIncludes(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, value: MaybeRefOrGetter<V>, comparator: UseArrayIncludesComparatorFn<T, V>): UseArrayIncludesReturn`

<details><summary>Code</summary>

```ts
export function useArrayIncludes<T, V = any>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  value: MaybeRefOrGetter<V>,
  comparator?: UseArrayIncludesComparatorFn<T, V>,
): UseArrayIncludesReturn
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.includes`
 *
 * @see https://vueuse.org/useArrayIncludes
 *
 * @returns true if the `value` is found in the array. Otherwise, false.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `value: MaybeRefOrGetter<V>`
  - `comparator: UseArrayIncludesComparatorFn<T, V>`
- **Return Type**: `UseArrayIncludesReturn`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseArrayIncludesOptions<T, V>`

<details><summary>Interface Code</summary>

```ts
export interface UseArrayIncludesOptions<T, V> {
  fromIndex?: number
  comparator?: UseArrayIncludesComparatorFn<T, V> | keyof T
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `fromIndex` | `number` | ✓ |  |
| `comparator` | `UseArrayIncludesComparatorFn<T, V> | keyof T` | ✓ |  |


---

## Type Aliases

### `UseArrayIncludesComparatorFn<T, V>`

```ts
type UseArrayIncludesComparatorFn<T, V> = ((element: T, value: V, index: number, array: MaybeRefOrGetter<T>[]) => boolean);
```

### `UseArrayIncludesReturn`

```ts
type UseArrayIncludesReturn = ComputedRef<boolean>;
```


---