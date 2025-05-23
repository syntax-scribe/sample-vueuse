[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useCycleList/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `WritableComputedRef` | `vue` |
| `toRef` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useCycleList(list: MaybeRefOrGetter<T[]>, options: UseCycleListOptions<T>): UseCycleListReturn<T>`

<details><summary>Code</summary>

```ts
export function useCycleList<T>(list: MaybeRefOrGetter<T[]>, options?: UseCycleListOptions<T>): UseCycleListReturn<T> {
  const state = shallowRef(getInitialValue()) as ShallowRef<T>
  const listRef = toRef(list)

  const index = computed<number>({
    get() {
      const targetList = listRef.value

      let index = options?.getIndexOf
        ? options.getIndexOf(state.value, targetList)
        : targetList.indexOf(state.value)

      if (index < 0)
        index = options?.fallbackIndex ?? 0

      return index
    },
    set(v) {
      set(v)
    },
  })

  function set(i: number) {
    const targetList = listRef.value
    const length = targetList.length
    const index = (i % length + length) % length
    const value = targetList[index]
    state.value = value
    return value
  }

  function shift(delta = 1) {
    return set(index.value + delta)
  }

  function next(n = 1) {
    return shift(n)
  }

  function prev(n = 1) {
    return shift(-n)
  }

  function getInitialValue() {
    return toValue(options?.initialValue ?? toValue<T[]>(list)[0]) ?? undefined
  }

  watch(listRef, () => set(index.value))

  return {
    state,
    index,
    next,
    prev,
    go: set,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Cycle through a list of items
 *
 * @see https://vueuse.org/useCycleList
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<T[]>`
  - `options: UseCycleListOptions<T>`
- **Return Type**: `UseCycleListReturn<T>`
- **Calls**:
  - `shallowRef (from vue)`
  - `getInitialValue`
  - `toRef (from @vueuse/shared)`
  - `computed (from vue)`
  - `options.getIndexOf`
  - `targetList.indexOf`
  - `set`
  - `shift`
  - `toValue (from vue)`
  - `watch (from vue)`
### `set(i: number): any`

<details><summary>Code</summary>

```ts
function set(i: number) {
    const targetList = listRef.value
    const length = targetList.length
    const index = (i % length + length) % length
    const value = targetList[index]
    state.value = value
    return value
  }
```
</details>

- **Parameters**:
  - `i: number`
- **Return Type**: `any`
### `shift(delta: number): any`

<details><summary>Code</summary>

```ts
function shift(delta = 1) {
    return set(index.value + delta)
  }
```
</details>

- **Parameters**:
  - `delta: number`
- **Return Type**: `any`
- **Calls**:
  - `set`
### `next(n: number): any`

<details><summary>Code</summary>

```ts
function next(n = 1) {
    return shift(n)
  }
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `any`
- **Calls**:
  - `shift`
### `prev(n: number): any`

<details><summary>Code</summary>

```ts
function prev(n = 1) {
    return shift(-n)
  }
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `any`
- **Calls**:
  - `shift`
### `getInitialValue(): any`

<details><summary>Code</summary>

```ts
function getInitialValue() {
    return toValue(options?.initialValue ?? toValue<T[]>(list)[0]) ?? undefined
  }
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `toValue (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseCycleListOptions<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseCycleListOptions<T> {
  /**
   * The initial value of the state.
   * A ref can be provided to reuse.
   */
  initialValue?: MaybeRef<T>

  /**
   * The default index when
   */
  fallbackIndex?: number

  /**
   * Custom function to get the index of the current value.
   */
  getIndexOf?: (value: T, list: T[]) => number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialValue` | `MaybeRef<T>` | ✓ |  |
| `fallbackIndex` | `number` | ✓ |  |
| `getIndexOf` | `(value: T, list: T[]) => number` | ✓ |  |

### `UseCycleListReturn<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseCycleListReturn<T> {
  state: ShallowRef<T>
  index: WritableComputedRef<number>
  next: (n?: number) => T
  prev: (n?: number) => T
  /**
   * Go to a specific index
   */
  go: (i: number) => T
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `state` | `ShallowRef<T>` | ✗ |  |
| `index` | `WritableComputedRef<number>` | ✗ |  |
| `next` | `(n?: number) => T` | ✗ |  |
| `prev` | `(n?: number) => T` | ✗ |  |
| `go` | `(i: number) => T` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---