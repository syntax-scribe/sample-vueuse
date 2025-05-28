[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 15 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 15 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 2 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 5 |
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
📂 **`packages/integrations/useAxios/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `AxiosInstance` | `axios` |
| `AxiosRequestConfig` | `axios` |
| `AxiosResponse` | `axios` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `noop` | `@vueuse/shared` |
| `until` | `@vueuse/shared` |
| `AxiosError` | `axios` |
| `axios` | `axios` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `url` | `string | undefined` | const | `typeof args[0] === 'string' ? args[0] : undefined` | ✗ |
| `argsPlaceholder` | `0 | 1` | const | `typeof url === 'string' ? 1 : 0` | ✗ |
| `defaultOptions` | `UseAxiosOptions<T>` | const | `{
    immediate: !!argsPlaceholder,
    shallow: true,
    abortPrevious: true,
  }` | ✗ |
| `defaultConfig` | `AxiosRequestConfig<D>` | let/var | `{}` | ✗ |
| `instance` | `AxiosInstance` | let/var | `axios` | ✗ |
| `options` | `UseAxiosOptions<T>` | let/var | `defaultOptions` | ✗ |
| `initialData` | `T` | const | `(options as UseAxiosOptionsWithInitialData<T>).initialData` | ✗ |
| `data` | `Ref<T>` | const | `(shallow ? shallowRef : deepRef)<T>(initialData!) as Ref<T>` | ✗ |
| `abortController` | `AbortController` | let/var | `new AbortController()` | ✗ |
| `promise` | `Promise<OverallUseAxiosReturn<T, R, D>>` | const | `{
    then: (...args) => waitUntilFinished().then(...args),
    catch: (...args) => waitUntilFinished().catch(...args),
  } as Promise<OverallUseAxiosReturn<T, R, D>>` | ✗ |
| `executeCounter` | `number` | let/var | `0` | ✗ |
| `_url` | `any` | const | `typeof executeUrl === 'string'
      ? executeUrl
      : url ?? config.url` | ✗ |
| `currentExecuteCounter` | `number` | const | `executeCounter` | ✗ |
| `result` | `any` | const | `r.data` | ✗ |
| `result` | `OverallUseAxiosReturn<T, R, D>` | const | `{
    response,
    data,
    error,
    isFinished,
    isLoading,
    cancel: abort,
    isAborted,
    isCanceled: isAborted,
    abort,
    execute,
  } as OverallUseAxiosReturn<T, R, D>` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `waitUntilFinished` | *none* | new Promise(...), until(isFinished).toBe(true).then |
| promise-chain | `execute` | *none* | instance(_url, { ...defaultConfig, ...typeof executeUrl === 'object' ? executeUrl : config, signal: abortController.signal })
      .then((r: any) => {
        if (isAborted.value)
          return
        response.value = r
        const result = r.data
        data.value = result
        onSuccess(result)
      })
      .catch((e: any) => {
        error.value = e
        onError(e)
      }).finally, instance(_url, { ...defaultConfig, ...typeof executeUrl === 'object' ? executeUrl : config, signal: abortController.signal })
      .then((r: any) => {
        if (isAborted.value)
          return
        response.value = r
        const result = r.data
        data.value = result
        onSuccess(result)
      }).catch, instance(_url, { ...defaultConfig, ...typeof executeUrl === 'object' ? executeUrl : config, signal: abortController.signal }).then |


---

## Functions

### `useAxios(url: string, config: AxiosRequestConfig<D>, options: O): StrictUseAxiosReturn<T, R, D, O> & Promise<StrictUseAxiosReturn<T, R, D, O>>`

<details><summary>Code</summary>

```ts
export function useAxios<T = any, R = AxiosResponse<T>, D = any, O extends UseAxiosOptionsWithInitialData<T> = UseAxiosOptionsWithInitialData<T>>(url: string, config?: AxiosRequestConfig<D>, options?: O): StrictUseAxiosReturn<T, R, D, O> & Promise<StrictUseAxiosReturn<T, R, D, O>>
```
</details>

- **Parameters**:
  - `url: string`
  - `config: AxiosRequestConfig<D>`
  - `options: O`
- **Return Type**: `StrictUseAxiosReturn<T, R, D, O> & Promise<StrictUseAxiosReturn<T, R, D, O>>`
### `isAxiosInstance(val: any): boolean`

<details><summary>Code</summary>

```ts
(val: any) => !!val?.request
```
</details>

- **Parameters**:
  - `val: any`
- **Return Type**: `boolean`
### `abort(message: string): void`

<details><summary>Code</summary>

```ts
(message?: string) => {
    if (isFinished.value || !isLoading.value)
      return

    abortController.abort(message)
    abortController = new AbortController()
    isAborted.value = true
    isLoading.value = false
    isFinished.value = false
  }
```
</details>

- **Parameters**:
  - `message: string`
- **Return Type**: `void`
- **Calls**:
  - `abortController.abort`
### `loading(loading: boolean): void`

<details><summary>Code</summary>

```ts
(loading: boolean) => {
    isLoading.value = loading
    isFinished.value = !loading
  }
```
</details>

- **Parameters**:
  - `loading: boolean`
- **Return Type**: `void`
### `resetData(): void`

<details><summary>Code</summary>

```ts
() => {
    if (resetOnExecute)
      data.value = initialData!
  }
```
</details>

- **Return Type**: `void`
### `waitUntilFinished(): Promise<OverallUseAxiosReturn<T, R, D>>`

<details><summary>Code</summary>

```ts
() =>
    new Promise<OverallUseAxiosReturn<T, R, D>>((resolve, reject) => {
      until(isFinished).toBe(true).then(() => error.value
        ? reject(error.value)
        // eslint-disable-next-line ts/no-use-before-define
        : resolve(result))
    })
```
</details>

- **Return Type**: `Promise<OverallUseAxiosReturn<T, R, D>>`
### `then(args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]): Promise<TResult1 | TResult2>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().then(...args)
```
</details>

- **Parameters**:
  - `args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]`
- **Return Type**: `Promise<TResult1 | TResult2>`
- **Calls**:
  - `waitUntilFinished().then`
### `catch(args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]): Promise<OverallUseAxiosReturn<T, R, D> | TResult>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().catch(...args)
```
</details>

- **Parameters**:
  - `args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]`
- **Return Type**: `Promise<OverallUseAxiosReturn<T, R, D> | TResult>`
- **Calls**:
  - `waitUntilFinished().catch`
### `then(args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]): Promise<TResult1 | TResult2>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().then(...args)
```
</details>

- **Parameters**:
  - `args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]`
- **Return Type**: `Promise<TResult1 | TResult2>`
- **Calls**:
  - `waitUntilFinished().then`
### `catch(args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]): Promise<OverallUseAxiosReturn<T, R, D> | TResult>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().catch(...args)
```
</details>

- **Parameters**:
  - `args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]`
- **Return Type**: `Promise<OverallUseAxiosReturn<T, R, D> | TResult>`
- **Calls**:
  - `waitUntilFinished().catch`
### `then(args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]): Promise<TResult1 | TResult2>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().then(...args)
```
</details>

- **Parameters**:
  - `args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]`
- **Return Type**: `Promise<TResult1 | TResult2>`
- **Calls**:
  - `waitUntilFinished().then`
### `catch(args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]): Promise<OverallUseAxiosReturn<T, R, D> | TResult>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().catch(...args)
```
</details>

- **Parameters**:
  - `args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]`
- **Return Type**: `Promise<OverallUseAxiosReturn<T, R, D> | TResult>`
- **Calls**:
  - `waitUntilFinished().catch`
### `then(args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]): Promise<TResult1 | TResult2>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().then(...args)
```
</details>

- **Parameters**:
  - `args: [onfulfilled?: (value: OverallUseAxiosReturn<T, R, D>) => TResult1 | PromiseLike<TResult1>, onrejected?: (reason: any) => TResult2 | PromiseLike<...>]`
- **Return Type**: `Promise<TResult1 | TResult2>`
- **Calls**:
  - `waitUntilFinished().then`
### `catch(args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]): Promise<OverallUseAxiosReturn<T, R, D> | TResult>`

<details><summary>Code</summary>

```ts
(...args) => waitUntilFinished().catch(...args)
```
</details>

- **Parameters**:
  - `args: [onrejected?: (reason: any) => TResult | PromiseLike<TResult>]`
- **Return Type**: `Promise<OverallUseAxiosReturn<T, R, D> | TResult>`
- **Calls**:
  - `waitUntilFinished().catch`
### `execute(executeUrl: string | AxiosRequestConfig<D> | undefined, config: AxiosRequestConfig<D>): Promise<OverallUseAxiosReturn<T, R, D>>`

<details><summary>Code</summary>

```ts
(executeUrl: string | AxiosRequestConfig<D> | undefined = url, config: AxiosRequestConfig<D> = {}) => {
    error.value = undefined
    const _url = typeof executeUrl === 'string'
      ? executeUrl
      : url ?? config.url

    if (_url === undefined) {
      error.value = new AxiosError(AxiosError.ERR_INVALID_URL)
      isFinished.value = true
      return promise
    }
    resetData()

    if (options.abortPrevious !== false)
      abort()

    loading(true)

    executeCounter += 1
    const currentExecuteCounter = executeCounter
    isAborted.value = false

    instance(_url, { ...defaultConfig, ...typeof executeUrl === 'object' ? executeUrl : config, signal: abortController.signal })
      .then((r: any) => {
        if (isAborted.value)
          return
        response.value = r
        const result = r.data
        data.value = result
        onSuccess(result)
      })
      .catch((e: any) => {
        error.value = e
        onError(e)
      })
      .finally(() => {
        options.onFinish?.()
        if (currentExecuteCounter === executeCounter)
          loading(false)
      })
    return promise
  }
```
</details>

- **Parameters**:
  - `executeUrl: string | AxiosRequestConfig<D> | undefined`
  - `config: AxiosRequestConfig<D>`
- **Return Type**: `Promise<OverallUseAxiosReturn<T, R, D>>`
- **Calls**:
  - `resetData`
  - `abort`
  - `loading`
  - `instance(_url, { ...defaultConfig, ...typeof executeUrl === 'object' ? executeUrl : config, signal: abortController.signal })
      .then((r: any) => {
        if (isAborted.value)
          return
        response.value = r
        const result = r.data
        data.value = result
        onSuccess(result)
      })
      .catch((e: any) => {
        error.value = e
        onError(e)
      })
      .finally`
  - `options.onFinish`

---

## Interfaces

### `UseAxiosReturn<T, R = AxiosResponse<T>, _D = any, O extends UseAxiosOptions = UseAxiosOptions<T>>`

<details><summary>Interface Code</summary>

```ts
export interface UseAxiosReturn<T, R = AxiosResponse<T>, _D = any, O extends UseAxiosOptions = UseAxiosOptions<T>> {
  /**
   * Axios Response
   */
  response: ShallowRef<R | undefined>

  /**
   * Axios response data
   */
  data: O extends UseAxiosOptionsWithInitialData<T> ? Ref<T> : Ref<T | undefined>

  /**
   * Indicates if the request has finished
   */
  isFinished: Ref<boolean>

  /**
   * Indicates if the request is currently loading
   */
  isLoading: Ref<boolean>

  /**
   * Indicates if the request was canceled
   */
  isAborted: Ref<boolean>

  /**
   * Any errors that may have occurred
   */
  error: ShallowRef<unknown | undefined>

  /**
   * Aborts the current request
   */
  abort: (message?: string | undefined) => void

  /**
   * Alias to `abort`
   */
  cancel: (message?: string | undefined) => void

  /**
   * Alias to `isAborted`
   */
  isCanceled: Ref<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `response` | `ShallowRef<R | undefined>` | ✗ |  |
| `data` | `O extends UseAxiosOptionsWithInitialData<T> ? Ref<T> : Ref<T | undefined>` | ✗ |  |
| `isFinished` | `Ref<boolean>` | ✗ |  |
| `isLoading` | `Ref<boolean>` | ✗ |  |
| `isAborted` | `Ref<boolean>` | ✗ |  |
| `error` | `ShallowRef<unknown | undefined>` | ✗ |  |
| `abort` | `(message?: string | undefined) => void` | ✗ |  |
| `cancel` | `(message?: string | undefined) => void` | ✗ |  |
| `isCanceled` | `Ref<boolean>` | ✗ |  |

### `StrictUseAxiosReturn<T, R, D, O extends UseAxiosOptions = UseAxiosOptions<T>>`

<details><summary>Interface Code</summary>

```ts
export interface StrictUseAxiosReturn<T, R, D, O extends UseAxiosOptions = UseAxiosOptions<T>> extends UseAxiosReturn<T, R, D, O> {
  /**
   * Manually call the axios request
   */
  execute: (url?: string | AxiosRequestConfig<D>, config?: AxiosRequestConfig<D>) => Promise<StrictUseAxiosReturn<T, R, D, O>>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `execute` | `(url?: string | AxiosRequestConfig<D>, config?: AxiosRequestConfig<D>) => Promise<StrictUseAxiosReturn<T, R, D, O>>` | ✗ |  |

### `EasyUseAxiosReturn<T, R, D>`

<details><summary>Interface Code</summary>

```ts
export interface EasyUseAxiosReturn<T, R, D> extends UseAxiosReturn<T, R, D> {
  /**
   * Manually call the axios request
   */
  execute: (url: string, config?: AxiosRequestConfig<D>) => Promise<EasyUseAxiosReturn<T, R, D>>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `execute` | `(url: string, config?: AxiosRequestConfig<D>) => Promise<EasyUseAxiosReturn<T, R, D>>` | ✗ |  |

### `UseAxiosOptionsBase<T = any>`

<details><summary>Interface Code</summary>

```ts
export interface UseAxiosOptionsBase<T = any> {
  /**
   * Will automatically run axios request when `useAxios` is used
   *
   */
  immediate?: boolean

  /**
   * Use shallowRef.
   *
   * @default true
   */
  shallow?: boolean

  /**
   * Abort previous request when a new request is made.
   *
   * @default true
   */
  abortPrevious?: boolean

  /**
   * Callback when error is caught.
   */
  onError?: (e: unknown) => void

  /**
   * Callback when success is caught.
   */
  onSuccess?: (data: T) => void

  /**
   * Sets the state to initialState before executing the promise.
   */
  resetOnExecute?: boolean

  /**
   * Callback when request is finished.
   */
  onFinish?: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |
| `shallow` | `boolean` | ✓ |  |
| `abortPrevious` | `boolean` | ✓ |  |
| `onError` | `(e: unknown) => void` | ✓ |  |
| `onSuccess` | `(data: T) => void` | ✓ |  |
| `resetOnExecute` | `boolean` | ✓ |  |
| `onFinish` | `() => void` | ✓ |  |

### `UseAxiosOptionsWithInitialData<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseAxiosOptionsWithInitialData<T> extends UseAxiosOptionsBase<T> {
  /**
   * Initial data
   */
  initialData: T
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialData` | `T` | ✗ |  |


---

## Type Aliases

### `UseAxiosOptions<T = any = any>`

```ts
type UseAxiosOptions<T = any = any> = UseAxiosOptionsBase<T> | UseAxiosOptionsWithInitialData<T>;
```

### `OverallUseAxiosReturn<T, R, D>`

```ts
type OverallUseAxiosReturn<T, R, D> = StrictUseAxiosReturn<T, R, D> | EasyUseAxiosReturn<T, R, D>;
```


---