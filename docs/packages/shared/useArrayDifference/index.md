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
- **Imports**: 4
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useArrayDifference/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `defaultComparator(value: T, othVal: T): boolean`

<details><summary>Code</summary>

```ts
function defaultComparator<T>(value: T, othVal: T) {
  return value === othVal
}
```
</details>

- **Parameters**:
  - `value: T`
  - `othVal: T`
- **Return Type**: `boolean`
### `useArrayDifference(list: MaybeRefOrGetter<T[]>, values: MaybeRefOrGetter<T[]>, key: keyof T, options: UseArrayDifferenceOptions): UseArrayDifferenceReturn<T>`

<details><summary>Code</summary>

```ts
export function useArrayDifference<T>(
  list: MaybeRefOrGetter<T[]>,
  values: MaybeRefOrGetter<T[]>,
  key?: keyof T,
  options?: UseArrayDifferenceOptions
): UseArrayDifferenceReturn<T>
```
</details>

- **Parameters**:
  - `list: MaybeRefOrGetter<T[]>`
  - `values: MaybeRefOrGetter<T[]>`
  - `key: keyof T`
  - `options: UseArrayDifferenceOptions`
- **Return Type**: `UseArrayDifferenceReturn<T>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseArrayDifferenceOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseArrayDifferenceOptions {
  /**
   * Returns asymmetric difference
   *
   * @see https://en.wikipedia.org/wiki/Symmetric_difference
   * @default false
   */
  symmetric?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `symmetric` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseArrayDifferenceReturn<T = any = any>`

```ts
type UseArrayDifferenceReturn<T = any = any> = ComputedRef<T[]>;
```


---