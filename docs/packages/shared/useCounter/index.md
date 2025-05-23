[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/useCounter/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `shallowReadonly` | `vue` |
| `shallowRef` | `vue` |
| `unref` | `vue` |


---

## Functions

### `useCounter(initialValue: MaybeRef<number>, options: UseCounterOptions): { count: any; inc: (delta?: number) => number; dec: (delta?: number) => number; get: () => any; set: (val: number) => number; reset: (val?: any) => number; }`

<details><summary>Code</summary>

```ts
export function useCounter(initialValue: MaybeRef<number> = 0, options: UseCounterOptions = {}) {
  let _initialValue = unref(initialValue)
  const count = shallowRef(initialValue)

  const {
    max = Number.POSITIVE_INFINITY,
    min = Number.NEGATIVE_INFINITY,
  } = options

  const inc = (delta = 1) => count.value = Math.max(Math.min(max, count.value + delta), min)
  const dec = (delta = 1) => count.value = Math.min(Math.max(min, count.value - delta), max)
  const get = () => count.value
  const set = (val: number) => (count.value = Math.max(min, Math.min(max, val)))
  const reset = (val = _initialValue) => {
    _initialValue = val
    return set(val)
  }

  return { count: shallowReadonly(count), inc, dec, get, set, reset }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Basic counter with utility functions.
 *
 * @see https://vueuse.org/useCounter
 * @param [initialValue]
 * @param options
 */
```

- **Parameters**:
  - `initialValue: MaybeRef<number>`
  - `options: UseCounterOptions`
- **Return Type**: `{ count: any; inc: (delta?: number) => number; dec: (delta?: number) => number; get: () => any; set: (val: number) => number; reset: (val?: any) => number; }`
- **Calls**:
  - `unref (from vue)`
  - `shallowRef (from vue)`
  - `Math.max`
  - `Math.min`
  - `set`
  - `shallowReadonly (from vue)`
### `inc(delta: number): number`

<details><summary>Code</summary>

```ts
(delta = 1) => count.value = Math.max(Math.min(max, count.value + delta), min)
```
</details>

- **Parameters**:
  - `delta: number`
- **Return Type**: `number`
### `dec(delta: number): number`

<details><summary>Code</summary>

```ts
(delta = 1) => count.value = Math.min(Math.max(min, count.value - delta), max)
```
</details>

- **Parameters**:
  - `delta: number`
- **Return Type**: `number`
### `get(): any`

<details><summary>Code</summary>

```ts
() => count.value
```
</details>

- **Return Type**: `any`
### `set(val: number): number`

<details><summary>Code</summary>

```ts
(val: number) => (count.value = Math.max(min, Math.min(max, val)))
```
</details>

- **Parameters**:
  - `val: number`
- **Return Type**: `number`
### `reset(val: any): number`

<details><summary>Code</summary>

```ts
(val = _initialValue) => {
    _initialValue = val
    return set(val)
  }
```
</details>

- **Parameters**:
  - `val: any`
- **Return Type**: `number`
- **Calls**:
  - `set`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseCounterOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseCounterOptions {
  min?: number
  max?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `min` | `number` | ✓ |  |
| `max` | `number` | ✓ |  |

### `UseCounterReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseCounterReturn {
  /**
   * The current value of the counter.
   */
  readonly count: Readonly<Ref<number>>
  /**
   * Increment the counter.
   *
   * @param {number} [delta=1] The number to increment.
   */
  inc: (delta?: number) => void
  /**
   * Decrement the counter.
   *
   * @param {number} [delta=1] The number to decrement.
   */
  dec: (delta?: number) => void
  /**
   * Get the current value of the counter.
   */
  get: () => number
  /**
   * Set the counter to a new value.
   *
   * @param val The new value of the counter.
   */
  set: (val: number) => void
  /**
   * Reset the counter to an initial value.
   */
  reset: (val?: number) => number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `count` | `Readonly<Ref<number>>` | ✗ |  |
| `inc` | `(delta?: number) => void` | ✗ |  |
| `dec` | `(delta?: number) => void` | ✗ |  |
| `get` | `() => number` | ✗ |  |
| `set` | `(val: number) => void` | ✗ |  |
| `reset` | `(val?: number) => number` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---