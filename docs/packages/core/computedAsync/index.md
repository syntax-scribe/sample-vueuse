[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/computedAsync/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `Ref` | `vue` |
| `noop` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `isRef` | `vue` |
| `shallowRef` | `vue` |
| `watchEffect` | `vue` |


---

## Functions

### `computedAsync(evaluationCallback: (onCancel: AsyncComputedOnCancel) => T | Promise<T>, initialState: T, optionsOrRef: AsyncComputedOptions & { lazy: true }): ComputedRef<T>`

<details><summary>Code</summary>

```ts
export function computedAsync<T>(
  evaluationCallback: (onCancel: AsyncComputedOnCancel) => T | Promise<T>,
  initialState: T,
  optionsOrRef: AsyncComputedOptions & { lazy: true },
): ComputedRef<T>
```
</details>

- **JSDoc**:
```ts
/**
 * Create an asynchronous computed dependency.
 *
 * @see https://vueuse.org/computedAsync
 * @param evaluationCallback     The promise-returning callback which generates the computed value
 * @param initialState           The initial state, used until the first evaluation finishes
 * @param optionsOrRef           Additional options or a ref passed to receive the updates of the async evaluation
 */
```

- **Parameters**:
  - `evaluationCallback: (onCancel: AsyncComputedOnCancel) => T | Promise<T>`
  - `initialState: T`
  - `optionsOrRef: AsyncComputedOptions & { lazy: true }`
- **Return Type**: `ComputedRef<T>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `AsyncComputedOptions`

<details><summary>Interface Code</summary>

```ts
export interface AsyncComputedOptions {
  /**
   * Should value be evaluated lazily
   *
   * @default false
   */
  lazy?: boolean

  /**
   * Ref passed to receive the updated of async evaluation
   */
  evaluating?: Ref<boolean>

  /**
   * Use shallowRef
   *
   * @default true
   */
  shallow?: boolean

  /**
   * The flush option allows for greater control over the timing of a history point, default to `pre`
   *
   * Possible values: `pre`, `post`, `sync`
   *
   * It works in the same way as the flush option in watch and watch effect in vue reactivity
   * @default 'pre'
   */
  flush?: 'pre' | 'post' | 'sync'

  /**
   * Callback when error is caught.
   */
  onError?: (e: unknown) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `lazy` | `boolean` | ✓ |  |
| `evaluating` | `Ref<boolean>` | ✓ |  |
| `shallow` | `boolean` | ✓ |  |
| `flush` | `'pre' | 'post' | 'sync'` | ✓ |  |
| `onError` | `(e: unknown) => void` | ✓ |  |


---

## Type Aliases

### `AsyncComputedOnCancel`

/**
 * Handle overlapping async evaluations.
 *
 * @param cancelCallback The provided callback is invoked when a re-evaluation of the computed value is triggered before the previous one finished
 */

```ts
type AsyncComputedOnCancel = (cancelCallback: Fn) => void;
```


---