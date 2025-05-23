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
- **Imports**: 14
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useOffsetPagination/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `UnwrapNestedRefs` | `vue` |
| `noop` | `@vueuse/shared` |
| `syncRef` | `@vueuse/shared` |
| `computed` | `vue` |
| `isReadonly` | `vue` |
| `isRef` | `vue` |
| `reactive` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `useClamp` | `../../math/useClamp` |


---

## Functions

### `useOffsetPagination(options: Omit<UseOffsetPaginationOptions, 'total'>): UseOffsetPaginationInfinityPageReturn`

<details><summary>Code</summary>

```ts
export function useOffsetPagination(options: Omit<UseOffsetPaginationOptions, 'total'>): UseOffsetPaginationInfinityPageReturn
```
</details>

- **Parameters**:
  - `options: Omit<UseOffsetPaginationOptions, 'total'>`
- **Return Type**: `UseOffsetPaginationInfinityPageReturn`
### `prev(): void`

<details><summary>Code</summary>

```ts
function prev() {
    currentPage.value--
  }
```
</details>

- **Return Type**: `void`
### `next(): void`

<details><summary>Code</summary>

```ts
function next() {
    currentPage.value++
  }
```
</details>

- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseOffsetPaginationOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseOffsetPaginationOptions {
  /**
   * Total number of items.
   */
  total?: MaybeRefOrGetter<number>

  /**
   * The number of items to display per page.
   * @default 10
   */
  pageSize?: MaybeRefOrGetter<number>

  /**
   * The current page number.
   * @default 1
   */
  page?: MaybeRef<number>

  /**
   * Callback when the `page` change.
   */
  onPageChange?: (returnValue: UnwrapNestedRefs<UseOffsetPaginationReturn>) => unknown

  /**
   * Callback when the `pageSize` change.
   */
  onPageSizeChange?: (returnValue: UnwrapNestedRefs<UseOffsetPaginationReturn>) => unknown

  /**
   * Callback when the `pageCount` change.
   */
  onPageCountChange?: (returnValue: UnwrapNestedRefs<UseOffsetPaginationReturn>) => unknown
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `total` | `MaybeRefOrGetter<number>` | ✓ |  |
| `pageSize` | `MaybeRefOrGetter<number>` | ✓ |  |
| `page` | `MaybeRef<number>` | ✓ |  |
| `onPageChange` | `(returnValue: UnwrapNestedRefs<UseOffsetPaginationReturn>) => unknown` | ✓ |  |
| `onPageSizeChange` | `(returnValue: UnwrapNestedRefs<UseOffsetPaginationReturn>) => unknown` | ✓ |  |
| `onPageCountChange` | `(returnValue: UnwrapNestedRefs<UseOffsetPaginationReturn>) => unknown` | ✓ |  |

### `UseOffsetPaginationReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseOffsetPaginationReturn {
  currentPage: Ref<number>
  currentPageSize: Ref<number>
  pageCount: ComputedRef<number>
  isFirstPage: ComputedRef<boolean>
  isLastPage: ComputedRef<boolean>
  prev: () => void
  next: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `currentPage` | `Ref<number>` | ✗ |  |
| `currentPageSize` | `Ref<number>` | ✗ |  |
| `pageCount` | `ComputedRef<number>` | ✗ |  |
| `isFirstPage` | `ComputedRef<boolean>` | ✗ |  |
| `isLastPage` | `ComputedRef<boolean>` | ✗ |  |
| `prev` | `() => void` | ✗ |  |
| `next` | `() => void` | ✗ |  |


---

## Type Aliases

### `UseOffsetPaginationInfinityPageReturn`

```ts
type UseOffsetPaginationInfinityPageReturn = Omit<UseOffsetPaginationReturn, 'isLastPage'>;
```


---