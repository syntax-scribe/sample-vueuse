[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 6 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `options` | `AsyncComputedOptions` | let/var | `*not shown*` | ✗ |
| `current` | `Ref<T>` | const | `(shallow ? shallowRef(initialState) : deepRef(initialState)) as Ref<T>` | ✗ |
| `counter` | `number` | let/var | `0` | ✗ |
| `counterAtBeginning` | `number` | let/var | `counter` | ✗ |
| `hasFinished` | `boolean` | let/var | `false` | ✗ |
| `result` | `Awaited<T>` | let/var | `await evaluationCallback((cancelCallback) => {
        onInvalidate(() => {
          if (evaluating)
            evaluating.value = false

          if (!hasFinished)
            cancelCallback()
        })
      })` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


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