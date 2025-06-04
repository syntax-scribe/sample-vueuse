[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 4 |
| ⚡ Async/Await Patterns | 4 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useAsyncState/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `UnwrapRef` | `vue` |
| `noop` | `@vueuse/shared` |
| `promiseTimeout` | `@vueuse/shared` |
| `until` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `state` | `any` | const | `shallow ? shallowRef(initialState) : deepRef(initialState)` | ✗ |
| `_promise` | `Promise<Data>` | let/var | `typeof promise === 'function'
      ? promise(...args as Params)
      : promise` | ✗ |
| `data` | `Awaited<Data>` | let/var | `await _promise` | ✗ |
| `shell` | `UseAsyncStateReturnBase<Data, Params, Shallow>` | const | `{
    state: state as Shallow extends true ? ShallowRef<Data> : Ref<UnwrapRef<Data>>,
    isReady,
    isLoading,
    error,
    execute,
  }` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `useAsyncState` | *none* | new Promise(...), until(isLoading).toBe(false).then(() => resolve(shell)).catch, until(isLoading).toBe(false).then, waitUntilIsLoaded().then |
| await-expression | `useAsyncState` | promiseTimeout(delay), _promise | *none* |
| async-function | `execute` | promiseTimeout(delay), _promise | *none* |
| promise-chain | `waitUntilIsLoaded` | *none* | new Promise(...), until(isLoading).toBe(false).then(() => resolve(shell)).catch, until(isLoading).toBe(false).then |


---

## Functions

### `useAsyncState(promise: Promise<Data> | ((...args: Params) => Promise<Data>), initialState: Data, options: UseAsyncStateOptions<Shallow, Data>): UseAsyncStateReturn<Data, Params, Shallow>`

<details><summary>Code</summary>

```ts
export function useAsyncState<Data, Params extends any[] = any[], Shallow extends boolean = true>(
  promise: Promise<Data> | ((...args: Params) => Promise<Data>),
  initialState: Data,
  options?: UseAsyncStateOptions<Shallow, Data>,
): UseAsyncStateReturn<Data, Params, Shallow> {
  const {
    immediate = true,
    delay = 0,
    onError = noop,
    onSuccess = noop,
    resetOnExecute = true,
    shallow = true,
    throwError,
  } = options ?? {}
  const state = shallow ? shallowRef(initialState) : deepRef(initialState)
  const isReady = shallowRef(false)
  const isLoading = shallowRef(false)
  const error = shallowRef<unknown | undefined>(undefined)

  async function execute(delay = 0, ...args: any[]) {
    if (resetOnExecute)
      state.value = initialState
    error.value = undefined
    isReady.value = false
    isLoading.value = true

    if (delay > 0)
      await promiseTimeout(delay)

    const _promise = typeof promise === 'function'
      ? promise(...args as Params)
      : promise

    try {
      const data = await _promise
      state.value = data
      isReady.value = true
      onSuccess(data)
    }
    catch (e) {
      error.value = e
      onError(e)
      if (throwError)
        throw e
    }
    finally {
      isLoading.value = false
    }

    return state.value as Data
  }

  if (immediate) {
    execute(delay)
  }

  const shell: UseAsyncStateReturnBase<Data, Params, Shallow> = {
    state: state as Shallow extends true ? ShallowRef<Data> : Ref<UnwrapRef<Data>>,
    isReady,
    isLoading,
    error,
    execute,
  }

  function waitUntilIsLoaded() {
    return new Promise<UseAsyncStateReturnBase<Data, Params, Shallow>>((resolve, reject) => {
      until(isLoading).toBe(false).then(() => resolve(shell)).catch(reject)
    })
  }

  return {
    ...shell,
    then(onFulfilled, onRejected) {
      return waitUntilIsLoaded()
        .then(onFulfilled, onRejected)
    },
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive async state. Will not block your setup function and will trigger changes once
 * the promise is ready.
 *
 * @see https://vueuse.org/useAsyncState
 * @param promise         The promise / async function to be resolved
 * @param initialState    The initial state, used until the first evaluation finishes
 * @param options
 */
```

- **Parameters**:
  - `promise: Promise<Data> | ((...args: Params) => Promise<Data>)`
  - `initialState: Data`
  - `options: UseAsyncStateOptions<Shallow, Data>`
- **Return Type**: `UseAsyncStateReturn<Data, Params, Shallow>`
- **Calls**:
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `promiseTimeout (from @vueuse/shared)`
  - `promise`
  - `onSuccess`
  - `onError`
  - `execute`
  - `until(isLoading).toBe(false).then(() => resolve(shell)).catch`
  - `waitUntilIsLoaded()
        .then`
### `execute(delay: number, args: any[]): Promise<Data>`

<details><summary>Code</summary>

```ts
async function execute(delay = 0, ...args: any[]) {
    if (resetOnExecute)
      state.value = initialState
    error.value = undefined
    isReady.value = false
    isLoading.value = true

    if (delay > 0)
      await promiseTimeout(delay)

    const _promise = typeof promise === 'function'
      ? promise(...args as Params)
      : promise

    try {
      const data = await _promise
      state.value = data
      isReady.value = true
      onSuccess(data)
    }
    catch (e) {
      error.value = e
      onError(e)
      if (throwError)
        throw e
    }
    finally {
      isLoading.value = false
    }

    return state.value as Data
  }
```
</details>

- **Parameters**:
  - `delay: number`
  - `args: any[]`
- **Return Type**: `Promise<Data>`
- **Calls**:
  - `promiseTimeout (from @vueuse/shared)`
  - `promise`
  - `onSuccess`
  - `onError`
### `waitUntilIsLoaded(): Promise<UseAsyncStateReturnBase<Data, Params, Shallow>>`

<details><summary>Code</summary>

```ts
function waitUntilIsLoaded() {
    return new Promise<UseAsyncStateReturnBase<Data, Params, Shallow>>((resolve, reject) => {
      until(isLoading).toBe(false).then(() => resolve(shell)).catch(reject)
    })
  }
```
</details>

- **Return Type**: `Promise<UseAsyncStateReturnBase<Data, Params, Shallow>>`
- **Calls**:
  - `until(isLoading).toBe(false).then(() => resolve(shell)).catch`

---

## Interfaces

### `UseAsyncStateReturnBase<Data, Params extends any[], Shallow extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncStateReturnBase<Data, Params extends any[], Shallow extends boolean> {
  state: Shallow extends true ? Ref<Data> : Ref<UnwrapRef<Data>>
  isReady: Ref<boolean>
  isLoading: Ref<boolean>
  error: Ref<unknown>
  execute: (delay?: number, ...args: Params) => Promise<Data>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `state` | `Shallow extends true ? Ref<Data> : Ref<UnwrapRef<Data>>` | ✗ |  |
| `isReady` | `Ref<boolean>` | ✗ |  |
| `isLoading` | `Ref<boolean>` | ✗ |  |
| `error` | `Ref<unknown>` | ✗ |  |
| `execute` | `(delay?: number, ...args: Params) => Promise<Data>` | ✗ |  |

### `UseAsyncStateOptions<Shallow extends boolean, D = any>`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncStateOptions<Shallow extends boolean, D = any> {
  /**
   * Delay for executing the promise. In milliseconds.
   *
   * @default 0
   */
  delay?: number

  /**
   * Execute the promise right after the function is invoked.
   * Will apply the delay if any.
   *
   * When set to false, you will need to execute it manually.
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Callback when error is caught.
   */
  onError?: (e: unknown) => void

  /**
   * Callback when success is caught.
   * @param {D} data
   */
  onSuccess?: (data: D) => void

  /**
   * Sets the state to initialState before executing the promise.
   *
   * This can be useful when calling the execute function more than once (for
   * example, to refresh data). When set to false, the current state remains
   * unchanged until the promise resolves.
   *
   * @default true
   */
  resetOnExecute?: boolean

  /**
   * Use shallowRef.
   *
   * @default true
   */
  shallow?: Shallow
  /**
   *
   * An error is thrown when executing the execute function
   *
   * @default false
   */
  throwError?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `delay` | `number` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `onError` | `(e: unknown) => void` | ✓ |  |
| `onSuccess` | `(data: D) => void` | ✓ |  |
| `resetOnExecute` | `boolean` | ✓ |  |
| `shallow` | `Shallow` | ✓ |  |
| `throwError` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseAsyncStateReturn<Data, Params extends any[] extends any[], Shallow extends boolean extends boolean>`

```ts
type UseAsyncStateReturn<Data, Params extends any[] extends any[], Shallow extends boolean extends boolean> = UseAsyncStateReturnBase<Data, Params, Shallow>
  & PromiseLike<UseAsyncStateReturnBase<Data, Params, Shallow>>;
```


---