[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 3 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useWebWorkerFn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `createWorkerBlobUrl` | `./lib/createWorkerBlobUrl` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `newWorker` | `Worker & { _url?: string }` | const | `new Worker(blobUrl)` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `useWebWorkerFn` | *none* | new Promise(...), Promise.reject |
| promise-chain | `callWorker` | *none* | new Promise(...) |
| promise-chain | `workerFn` | *none* | Promise.reject |


---

## Functions

### `useWebWorkerFn(fn: T, options: UseWebWorkerOptions): { workerFn: (...fnArgs: Parameters<T>) => Promise<ReturnType<T>>; workerStatus: any; workerTerminate: (status?: WebWorkerStatus) => void; }`

<details><summary>Code</summary>

```ts
export function useWebWorkerFn<T extends (...fnArgs: any[]) => any>(fn: T, options: UseWebWorkerOptions = {}) {
  const {
    dependencies = [],
    localDependencies = [],
    timeout,
    window = defaultWindow,
  } = options

  const worker = deepRef<(Worker & { _url?: string }) | undefined>()
  const workerStatus = shallowRef<WebWorkerStatus>('PENDING')
  const promise = deepRef<({ reject?: (result: ReturnType<T> | ErrorEvent) => void, resolve?: (result: ReturnType<T>) => void })>({})
  const timeoutId = shallowRef<number>()

  const workerTerminate = (status: WebWorkerStatus = 'PENDING') => {
    if (worker.value && worker.value._url && window) {
      worker.value.terminate()
      URL.revokeObjectURL(worker.value._url)
      promise.value = {}
      worker.value = undefined
      window.clearTimeout(timeoutId.value)
      workerStatus.value = status
    }
  }

  workerTerminate()

  tryOnScopeDispose(workerTerminate)

  const generateWorker = () => {
    const blobUrl = createWorkerBlobUrl(fn, dependencies, localDependencies)
    const newWorker: Worker & { _url?: string } = new Worker(blobUrl)
    newWorker._url = blobUrl

    newWorker.onmessage = (e: MessageEvent) => {
      const { resolve = () => { }, reject = () => { } } = promise.value
      const [status, result] = e.data as [WebWorkerStatus, ReturnType<T>]

      switch (status) {
        case 'SUCCESS':
          resolve(result)
          workerTerminate(status)
          break
        default:
          reject(result)
          workerTerminate('ERROR')
          break
      }
    }

    newWorker.onerror = (e: ErrorEvent) => {
      const { reject = () => { } } = promise.value
      e.preventDefault()
      reject(e)
      workerTerminate('ERROR')
    }

    if (timeout) {
      timeoutId.value = setTimeout(
        () => workerTerminate('TIMEOUT_EXPIRED'),
        timeout,
      ) as any
    }
    return newWorker
  }

  const callWorker = (...fnArgs: Parameters<T>) => new Promise<ReturnType<T>>((resolve, reject) => {
    promise.value = {
      resolve,
      reject,
    }
    worker.value?.postMessage([[...fnArgs]])

    workerStatus.value = 'RUNNING'
  })

  const workerFn = (...fnArgs: Parameters<T>) => {
    if (workerStatus.value === 'RUNNING') {
      console.error(
        '[useWebWorkerFn] You can only run one instance of the worker at a time.',
      )
      /* eslint-disable-next-line prefer-promise-reject-errors */
      return Promise.reject()
    }

    worker.value = generateWorker()
    return callWorker(...fnArgs)
  }

  return {
    workerFn,
    workerStatus,
    workerTerminate,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Run expensive function without blocking the UI, using a simple syntax that makes use of Promise.
 *
 * @see https://vueuse.org/useWebWorkerFn
 * @param fn
 * @param options
 */
```

- **Parameters**:
  - `fn: T`
  - `options: UseWebWorkerOptions`
- **Return Type**: `{ workerFn: (...fnArgs: Parameters<T>) => Promise<ReturnType<T>>; workerStatus: any; workerTerminate: (status?: WebWorkerStatus) => void; }`
- **Calls**:
  - `deepRef (from vue)`
  - `shallowRef (from vue)`
  - `worker.value.terminate`
  - `URL.revokeObjectURL`
  - `window.clearTimeout`
  - `workerTerminate`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `createWorkerBlobUrl (from ./lib/createWorkerBlobUrl)`
  - `resolve`
  - `reject`
  - `e.preventDefault`
  - `setTimeout`
  - `worker.value?.postMessage`
  - `console.error`
  - `Promise.reject`
  - `generateWorker`
  - `callWorker`
- **Internal Comments**:
```
/* eslint-disable-next-line prefer-promise-reject-errors */
```

### `workerTerminate(status: WebWorkerStatus): void`

<details><summary>Code</summary>

```ts
(status: WebWorkerStatus = 'PENDING') => {
    if (worker.value && worker.value._url && window) {
      worker.value.terminate()
      URL.revokeObjectURL(worker.value._url)
      promise.value = {}
      worker.value = undefined
      window.clearTimeout(timeoutId.value)
      workerStatus.value = status
    }
  }
```
</details>

- **Parameters**:
  - `status: WebWorkerStatus`
- **Return Type**: `void`
- **Calls**:
  - `worker.value.terminate`
  - `URL.revokeObjectURL`
  - `window.clearTimeout`
### `generateWorker(): Worker & { _url?: string; }`

<details><summary>Code</summary>

```ts
() => {
    const blobUrl = createWorkerBlobUrl(fn, dependencies, localDependencies)
    const newWorker: Worker & { _url?: string } = new Worker(blobUrl)
    newWorker._url = blobUrl

    newWorker.onmessage = (e: MessageEvent) => {
      const { resolve = () => { }, reject = () => { } } = promise.value
      const [status, result] = e.data as [WebWorkerStatus, ReturnType<T>]

      switch (status) {
        case 'SUCCESS':
          resolve(result)
          workerTerminate(status)
          break
        default:
          reject(result)
          workerTerminate('ERROR')
          break
      }
    }

    newWorker.onerror = (e: ErrorEvent) => {
      const { reject = () => { } } = promise.value
      e.preventDefault()
      reject(e)
      workerTerminate('ERROR')
    }

    if (timeout) {
      timeoutId.value = setTimeout(
        () => workerTerminate('TIMEOUT_EXPIRED'),
        timeout,
      ) as any
    }
    return newWorker
  }
```
</details>

- **Return Type**: `Worker & { _url?: string; }`
- **Calls**:
  - `createWorkerBlobUrl (from ./lib/createWorkerBlobUrl)`
  - `resolve`
  - `workerTerminate`
  - `reject`
  - `e.preventDefault`
  - `setTimeout`
### `callWorker(fnArgs: Parameters<T>): Promise<ReturnType<T>>`

<details><summary>Code</summary>

```ts
(...fnArgs: Parameters<T>) => new Promise<ReturnType<T>>((resolve, reject) => {
    promise.value = {
      resolve,
      reject,
    }
    worker.value?.postMessage([[...fnArgs]])

    workerStatus.value = 'RUNNING'
  })
```
</details>

- **Parameters**:
  - `fnArgs: Parameters<T>`
- **Return Type**: `Promise<ReturnType<T>>`
### `workerFn(fnArgs: Parameters<T>): Promise<ReturnType<T>>`

<details><summary>Code</summary>

```ts
(...fnArgs: Parameters<T>) => {
    if (workerStatus.value === 'RUNNING') {
      console.error(
        '[useWebWorkerFn] You can only run one instance of the worker at a time.',
      )
      /* eslint-disable-next-line prefer-promise-reject-errors */
      return Promise.reject()
    }

    worker.value = generateWorker()
    return callWorker(...fnArgs)
  }
```
</details>

- **Parameters**:
  - `fnArgs: Parameters<T>`
- **Return Type**: `Promise<ReturnType<T>>`
- **Calls**:
  - `console.error`
  - `Promise.reject`
  - `generateWorker`
  - `callWorker`
- **Internal Comments**:
```
/* eslint-disable-next-line prefer-promise-reject-errors */
```


---

## Interfaces

### `UseWebWorkerOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseWebWorkerOptions extends ConfigurableWindow {
  /**
   * Number of milliseconds before killing the worker
   *
   * @default undefined
   */
  timeout?: number
  /**
   * An array that contains the external dependencies needed to run the worker
   */
  dependencies?: string[]
  /**
   * An array that contains the local dependencies needed to run the worker
   */
  localDependencies?: Function[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `timeout` | `number` | ✓ |  |
| `dependencies` | `string[]` | ✓ |  |
| `localDependencies` | `Function[]` | ✓ |  |


---

## Type Aliases

### `WebWorkerStatus`

```ts
type WebWorkerStatus = | 'PENDING'
  | 'SUCCESS'
  | 'RUNNING'
  | 'ERROR'
  | 'TIMEOUT_EXPIRED';
```

### `UseWebWorkerFnReturn`

```ts
type UseWebWorkerFnReturn = ReturnType<typeof useWebWorkerFn>;
```


---