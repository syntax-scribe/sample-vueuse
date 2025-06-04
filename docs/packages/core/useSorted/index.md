[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `compareFn` | `UseSortedCompareFn` | let/var | `defaultCompare` | ✗ |
| `options` | `UseSortedOptions` | let/var | `{}` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


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