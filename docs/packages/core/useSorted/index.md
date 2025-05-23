[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/useSorted/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `computed` | `vue` |
| `isRef` | `vue` |
| `toValue` | `vue` |
| `watchEffect` | `vue` |


---

## Functions

### `defaultSortFn(source: T[], compareFn: UseSortedCompareFn<T>): T[]`

<details><summary>Code</summary>

```ts
<T>(source: T[], compareFn: UseSortedCompareFn<T>): T[] => source.sort(compareFn)
```
</details>

- **Parameters**:
  - `source: T[]`
  - `compareFn: UseSortedCompareFn<T>`
- **Return Type**: `T[]`
- **Calls**:
  - `source.sort`
### `defaultCompare(a: number, b: number): number`

<details><summary>Code</summary>

```ts
(a, b) => a - b
```
</details>

- **Parameters**:
  - `a: number`
  - `b: number`
- **Return Type**: `number`
### `useSorted(source: MaybeRefOrGetter<T[]>, compareFn: UseSortedCompareFn<T>): Ref<T[]>`

<details><summary>Code</summary>

```ts
export function useSorted<T = any>(source: MaybeRefOrGetter<T[]>, compareFn?: UseSortedCompareFn<T>): Ref<T[]>
```
</details>

- **JSDoc**:
```ts
/**
 * reactive sort array
 *
 * @see https://vueuse.org/useSorted
 */
```

- **Parameters**:
  - `source: MaybeRefOrGetter<T[]>`
  - `compareFn: UseSortedCompareFn<T>`
- **Return Type**: `Ref<T[]>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseSortedOptions<T = any>`

<details><summary>Interface Code</summary>

```ts
export interface UseSortedOptions<T = any> {
  /**
   * sort algorithm
   */
  sortFn?: UseSortedFn<T>
  /**
   * compare function
   */
  compareFn?: UseSortedCompareFn<T>
  /**
   * change the value of the source array
   * @default false
   */
  dirty?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `sortFn` | `UseSortedFn<T>` | ✓ |  |
| `compareFn` | `UseSortedCompareFn<T>` | ✓ |  |
| `dirty` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseSortedCompareFn<T = any = any>`

```ts
type UseSortedCompareFn<T = any = any> = (a: T, b: T) => number;
```

### `UseSortedFn<T = any = any>`

```ts
type UseSortedFn<T = any = any> = (arr: T[], compareFn: UseSortedCompareFn<T>) => T[];
```


---