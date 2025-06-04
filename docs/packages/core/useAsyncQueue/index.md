[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |
| ⚡ Async/Await Patterns | 2 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 3 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useAsyncQueue/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `noop` | `@vueuse/shared` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `promiseState` | `Record<
    UseAsyncQueueResult<T>['state'],
    UseAsyncQueueResult<T>['state']
  >` | const | `{
    aborted: 'aborted',
    fulfilled: 'fulfilled',
    pending: 'pending',
    rejected: 'rejected',
  }` | ✗ |
| `result` | `{ [P in keyof T]: UseAsyncQueueResult<T[P]>; }` | const | `reactive(initialResult) as { [P in keyof T]: UseAsyncQueueResult<T[P]> }` | ✗ |
| `error` | `Error` | const | `new Error('aborted')` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `useAsyncQueue` | *none* | prev
      .then((prevRes) => {
        if (signal?.aborted) {
          updateResult(promiseState.aborted, new Error('aborted'))
          return
        }

        if (
          result[activeIndex.value]?.state === promiseState.rejected
          && interrupt
        ) {
          onFinished()
          return
        }

        const done = curr(prevRes).then((currentRes: any) => {
          updateResult(promiseState.fulfilled, currentRes)
          if (activeIndex.value === tasks.length - 1)
            onFinished()
          return currentRes
        })

        if (!signal)
          return done

        return Promise.race([done, whenAborted(signal)])
      }).catch, prev.then, curr(prevRes).then, Promise.race, Promise.resolve |
| promise-chain | `whenAborted` | *none* | new Promise(...) |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |


---

## Functions

### `useAsyncQueue(tasks: S & Array<UseAsyncQueueTask<any>>, options: UseAsyncQueueOptions): UseAsyncQueueReturn<{ [P in keyof T]: UseAsyncQueueResult<T[P]> }>`

<details><summary>Code</summary>

```ts
export function useAsyncQueue<T extends any[], S = MapQueueTask<T>>(
  tasks: S & Array<UseAsyncQueueTask<any>>,
  options?: UseAsyncQueueOptions,
): UseAsyncQueueReturn<{ [P in keyof T]: UseAsyncQueueResult<T[P]> }> {
  const {
    interrupt = true,
    onError = noop,
    onFinished = noop,
    signal,
  } = options || {}

  const promiseState: Record<
    UseAsyncQueueResult<T>['state'],
    UseAsyncQueueResult<T>['state']
  > = {
    aborted: 'aborted',
    fulfilled: 'fulfilled',
    pending: 'pending',
    rejected: 'rejected',
  }

  const initialResult = Array.from(Array.from({ length: tasks.length }), () => ({ state: promiseState.pending, data: null }))

  const result = reactive(initialResult) as { [P in keyof T]: UseAsyncQueueResult<T[P]> }

  const activeIndex = shallowRef<number>(-1)

  if (!tasks || tasks.length === 0) {
    onFinished()
    return {
      activeIndex,
      result,
    }
  }

  function updateResult(state: UseAsyncQueueResult<T>['state'], res: unknown) {
    activeIndex.value++
    result[activeIndex.value].data = res as T
    result[activeIndex.value].state = state
  }

  tasks.reduce((prev, curr) => {
    return prev
      .then((prevRes) => {
        if (signal?.aborted) {
          updateResult(promiseState.aborted, new Error('aborted'))
          return
        }

        if (
          result[activeIndex.value]?.state === promiseState.rejected
          && interrupt
        ) {
          onFinished()
          return
        }

        const done = curr(prevRes).then((currentRes: any) => {
          updateResult(promiseState.fulfilled, currentRes)
          if (activeIndex.value === tasks.length - 1)
            onFinished()
          return currentRes
        })

        if (!signal)
          return done

        return Promise.race([done, whenAborted(signal)])
      })
      .catch((e) => {
        if (signal?.aborted) {
          updateResult(promiseState.aborted, e)
          return e
        }

        updateResult(promiseState.rejected, e)
        onError()
        return e
      })
  }, Promise.resolve())

  return {
    activeIndex,
    result,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Asynchronous queue task controller.
 *
 * @see https://vueuse.org/useAsyncQueue
 * @param tasks
 * @param options
 */
```

- **Parameters**:
  - `tasks: S & Array<UseAsyncQueueTask<any>>`
  - `options: UseAsyncQueueOptions`
- **Return Type**: `UseAsyncQueueReturn<{ [P in keyof T]: UseAsyncQueueResult<T[P]> }>`
- **Calls**:
  - `Array.from`
  - `reactive (from vue)`
  - `shallowRef (from vue)`
  - `onFinished`
  - `tasks.reduce`
  - `prev
      .then((prevRes) => {
        if (signal?.aborted) {
          updateResult(promiseState.aborted, new Error('aborted'))
          return
        }

        if (
          result[activeIndex.value]?.state === promiseState.rejected
          && interrupt
        ) {
          onFinished()
          return
        }

        const done = curr(prevRes).then((currentRes: any) => {
          updateResult(promiseState.fulfilled, currentRes)
          if (activeIndex.value === tasks.length - 1)
            onFinished()
          return currentRes
        })

        if (!signal)
          return done

        return Promise.race([done, whenAborted(signal)])
      })
      .catch`
  - `updateResult`
  - `onError`
  - `Promise.resolve`
### `updateResult(state: UseAsyncQueueResult<T>['state'], res: unknown): void`

<details><summary>Code</summary>

```ts
function updateResult(state: UseAsyncQueueResult<T>['state'], res: unknown) {
    activeIndex.value++
    result[activeIndex.value].data = res as T
    result[activeIndex.value].state = state
  }
```
</details>

- **Parameters**:
  - `state: UseAsyncQueueResult<T>['state']`
  - `res: unknown`
- **Return Type**: `void`
### `whenAborted(signal: AbortSignal): Promise<never>`

<details><summary>Code</summary>

```ts
function whenAborted(signal: AbortSignal): Promise<never> {
  return new Promise((resolve, reject) => {
    const error = new Error('aborted')

    if (signal.aborted)
      reject(error)
    else
      signal.addEventListener('abort', () => reject(error), { once: true })
  })
}
```
</details>

- **Parameters**:
  - `signal: AbortSignal`
- **Return Type**: `Promise<never>`
- **Calls**:
  - `reject`
  - `signal.addEventListener`

---

## Interfaces

### `UseAsyncQueueResult<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncQueueResult<T> {
  state: 'aborted' | 'fulfilled' | 'pending' | 'rejected'
  data: T | null
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `state` | `'aborted' | 'fulfilled' | 'pending' | 'rejected'` | ✗ |  |
| `data` | `T | null` | ✗ |  |

### `UseAsyncQueueReturn<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncQueueReturn<T> {
  activeIndex: ShallowRef<number>
  result: T
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `activeIndex` | `ShallowRef<number>` | ✗ |  |
| `result` | `T` | ✗ |  |

### `UseAsyncQueueOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseAsyncQueueOptions {
  /**
   * Interrupt tasks when current task fails.
   *
   * @default true
   */
  interrupt?: boolean

  /**
   * Trigger it when the tasks fails.
   *
   */
  onError?: () => void

  /**
   * Trigger it when the tasks ends.
   *
   */
  onFinished?: () => void

  /**
   * A AbortSignal that can be used to abort the task.
   */
  signal?: AbortSignal
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `interrupt` | `boolean` | ✓ |  |
| `onError` | `() => void` | ✓ |  |
| `onFinished` | `() => void` | ✓ |  |
| `signal` | `AbortSignal` | ✓ |  |


---

## Type Aliases

### `UseAsyncQueueTask<T>`

```ts
type UseAsyncQueueTask<T> = (...args: any[]) => T | Promise<T>;
```

### `MapQueueTask<T extends any[] extends any[]>`

```ts
type MapQueueTask<T extends any[] extends any[]> = {
  [K in keyof T]: UseAsyncQueueTask<T[K]>
};
```


---