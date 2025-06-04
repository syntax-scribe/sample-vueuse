[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 26 |
| 📦 Imports | 18 |
| 📊 Variables & Constants | 23 |
| ⚡ Async/Await Patterns | 5 |
| 🟢 Vue Composition API | 4 |
| 📐 Interfaces | 7 |
| 📑 Type Aliases | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useFetch/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `EventHookOn` | `@vueuse/shared` |
| `Fn` | `@vueuse/shared` |
| `Stoppable` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `containsProp` | `@vueuse/shared` |
| `createEventHook` | `@vueuse/shared` |
| `toRef` | `@vueuse/shared` |
| `until` | `@vueuse/shared` |
| `useTimeoutFn` | `@vueuse/shared` |
| `computed` | `vue` |
| `isRef` | `vue` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `payloadMapping` | `Record<string, string>` | const | `{
  json: 'application/json',
  text: 'text/plain',
}` | ✗ |
| `reAbsolute` | `RegExp` | const | `/^(?:[a-z][a-z\d+\-.]*:)?\/\//i` | ✗ |
| `callback` | `any` | let/var | `*not shown*` | ✗ |
| `_combination` | `Combination` | const | `config.combination || 'chain' as Combination` | ✗ |
| `_options` | `UseFetchOptions` | const | `config.options || {}` | ✗ |
| `_fetchOptions` | `RequestInit` | const | `config.fetchOptions || {}` | ✗ |
| `options` | `UseFetchOptions` | let/var | `_options` | ✗ |
| `fetchOptions` | `RequestInit` | let/var | `_fetchOptions` | ✗ |
| `supportsAbort` | `boolean` | const | `typeof AbortController === 'function'` | ✗ |
| `fetchOptions` | `RequestInit` | let/var | `{}` | ✗ |
| `options` | `UseFetchOptions` | let/var | `{
    immediate: true,
    refetch: false,
    timeout: 0,
    updateDataOnError: false,
  }` | ✗ |
| `config` | `InternalConfig` | const | `{
    method: 'GET',
    type: 'text' as DataType,
    payload: undefined as unknown,
  }` | ✗ |
| `controller` | `AbortController | undefined` | let/var | `*not shown*` | ✗ |
| `timer` | `Stoppable | undefined` | let/var | `*not shown*` | ✗ |
| `executeCounter` | `number` | let/var | `0` | ✗ |
| `currentExecuteCounter` | `number` | let/var | `executeCounter` | ✗ |
| `defaultFetchOptions` | `RequestInit` | let/var | `{
      method: config.method,
      headers: {},
    }` | ✗ |
| `headers` | `Record<string, string>` | let/var | `headersToObject(defaultFetchOptions.headers) as Record<string, string>` | ✗ |
| `isCanceled` | `boolean` | let/var | `false` | ✗ |
| `context` | `BeforeFetchContext` | let/var | `{
      url: toValue(url),
      options: {
        ...defaultFetchOptions,
        ...fetchOptions,
      },
      cancel: () => { isCanceled = true },
    }` | ✗ |
| `responseData` | `any` | let/var | `null` | ✗ |
| `errorData` | `any` | let/var | `fetchError.message || fetchError.name` | ✗ |
| `shell` | `UseFetchReturn<T>` | const | `{
    isFinished: readonly(isFinished),
    isFetching: readonly(isFetching),
    statusCode,
    response,
    error,
    data,
    canAbort,
    aborted,
    abort,
    execute,

    onFetchResponse: responseEvent.on,
    onFetchError: errorEvent.on,
    onFetchFinally: finallyEvent.on,
    // method
    get: setMethod('GET'),
    put: setMethod('PUT'),
    post: setMethod('POST'),
    delete: setMethod('DELETE'),
    patch: setMethod('PATCH'),
    head: setMethod('HEAD'),
    options: setMethod('OPTIONS'),
    // type
    json: setType('json'),
    text: setType('text'),
    blob: setType('blob'),
    arrayBuffer: setType('arrayBuffer'),
    formData: setType('formData'),
  }` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `combineCallbacks` | callback(ctx), callback(ctx) | *none* |
| async-function | `execute` | options.beforeFetch(context), fetchResponse.clone()[config.type](), options.afterFetch({
            data: responseData,
            response: fetchResponse,
            context,
            execute,
          }), options.onFetchError({
            data: responseData,
            error: fetchError,
            response: response.value,
            context,
            execute,
          }) | Promise.resolve, fetch(
      context.url,
      {
        ...defaultFetchOptions,
        ...context.options,
        headers: {
          ...headersToObject(defaultFetchOptions.headers),
          ...headersToObject(context.options?.headers),
        },
      },
    )
      .then(async (fetchResponse) => {
        response.value = fetchResponse
        statusCode.value = fetchResponse.status

        responseData = await fetchResponse.clone()[config.type]()

        // see: https://www.tjvantoll.com/2015/09/13/fetch-and-errors/
        if (!fetchResponse.ok) {
          data.value = initialData || null
          throw new Error(fetchResponse.statusText)
        }

        if (options.afterFetch) {
          ({ data: responseData } = await options.afterFetch({
            data: responseData,
            response: fetchResponse,
            context,
            execute,
          }))
        }
        data.value = responseData

        responseEvent.trigger(fetchResponse)
        return fetchResponse
      })
      .catch(async (fetchError) => {
        let errorData = fetchError.message || fetchError.name

        if (options.onFetchError) {
          ({ error: errorData, data: responseData } = await options.onFetchError({
            data: responseData,
            error: fetchError,
            response: response.value,
            context,
            execute,
          }))
        }

        error.value = errorData
        if (options.updateDataOnError)
          data.value = responseData

        errorEvent.trigger(fetchError)
        if (throwOnFailed)
          throw fetchError
        return null
      }).finally, fetch(
      context.url,
      {
        ...defaultFetchOptions,
        ...context.options,
        headers: {
          ...headersToObject(defaultFetchOptions.headers),
          ...headersToObject(context.options?.headers),
        },
      },
    )
      .then(async (fetchResponse) => {
        response.value = fetchResponse
        statusCode.value = fetchResponse.status

        responseData = await fetchResponse.clone()[config.type]()

        // see: https://www.tjvantoll.com/2015/09/13/fetch-and-errors/
        if (!fetchResponse.ok) {
          data.value = initialData || null
          throw new Error(fetchResponse.statusText)
        }

        if (options.afterFetch) {
          ({ data: responseData } = await options.afterFetch({
            data: responseData,
            response: fetchResponse,
            context,
            execute,
          }))
        }
        data.value = responseData

        responseEvent.trigger(fetchResponse)
        return fetchResponse
      }).catch, fetch(
      context.url,
      {
        ...defaultFetchOptions,
        ...context.options,
        headers: {
          ...headersToObject(defaultFetchOptions.headers),
          ...headersToObject(context.options?.headers),
        },
      },
    ).then |
| promise-chain | `setMethod` | *none* | waitUntilFinished().then |
| promise-chain | `waitUntilFinished` | *none* | new Promise(...), until(isFinished).toBe(true).then(() => resolve(shell)).catch, until(isFinished).toBe(true).then |
| promise-chain | `setType` | *none* | waitUntilFinished().then |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `isFetchOptions(obj: object): obj is UseFetchOptions`

<details><summary>Code</summary>

```ts
function isFetchOptions(obj: object): obj is UseFetchOptions {
  return obj && containsProp(obj, 'immediate', 'refetch', 'initialData', 'timeout', 'beforeFetch', 'afterFetch', 'onFetchError', 'fetch', 'updateDataOnError')
}
```
</details>

- **JSDoc**:
```ts
/**
 * !!!IMPORTANT!!!
 *
 * If you update the UseFetchOptions interface, be sure to update this object
 * to include the new options
 */
```

- **Parameters**:
  - `obj: object`
- **Return Type**: `obj is UseFetchOptions`
- **Calls**:
  - `containsProp (from @vueuse/shared)`
### `isAbsoluteURL(url: string): boolean`

<details><summary>Code</summary>

```ts
function isAbsoluteURL(url: string) {
  return reAbsolute.test(url)
}
```
</details>

- **Parameters**:
  - `url: string`
- **Return Type**: `boolean`
- **Calls**:
  - `reAbsolute.test`
### `headersToObject(headers: HeadersInit | undefined): HeadersInit`

<details><summary>Code</summary>

```ts
function headersToObject(headers: HeadersInit | undefined) {
  if (typeof Headers !== 'undefined' && headers instanceof Headers)
    return Object.fromEntries(headers.entries())
  return headers
}
```
</details>

- **Parameters**:
  - `headers: HeadersInit | undefined`
- **Return Type**: `HeadersInit`
- **Calls**:
  - `Object.fromEntries`
  - `headers.entries`
### `combineCallbacks(combination: Combination, callbacks: (((ctx: T) => void | Partial<T> | Promise<void | Partial<T>>) | undefined)[]): (ctx: T) => Promise<any>`

<details><summary>Code</summary>

```ts
function combineCallbacks<T = any>(combination: Combination, ...callbacks: (((ctx: T) => void | Partial<T> | Promise<void | Partial<T>>) | undefined)[]) {
  if (combination === 'overwrite') {
    // use last callback
    return async (ctx: T) => {
      let callback
      for (let i = callbacks.length - 1; i >= 0; i--) {
        if (callbacks[i] != null) {
          callback = callbacks[i]
          break
        }
      }
      if (callback)
        return { ...ctx, ...(await callback(ctx)) }

      return ctx
    }
  }
  else {
    // chaining and combine result
    return async (ctx: T) => {
      for (const callback of callbacks) {
        if (callback)
          ctx = { ...ctx, ...(await callback(ctx)) }
      }

      return ctx
    }
  }
}
```
</details>

- **Parameters**:
  - `combination: Combination`
  - `callbacks: (((ctx: T) => void | Partial<T> | Promise<void | Partial<T>>) | undefined)[]`
- **Return Type**: `(ctx: T) => Promise<any>`
- **Calls**:
  - `callback`
- **Internal Comments**:
```
// use last callback
// chaining and combine result
```

### `createFetch(config: CreateFetchOptions): { <T>(url: MaybeRefOrGetter<string>): UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>; <T>(url: MaybeRefOrGetter<string>, useFetchOptions: UseFetchOptions): UseFetchReturn<...> & PromiseLike<...>; <T>(url: MaybeRefOrGetter<...>, options: RequestInit, useFetchOptions?: UseFetchOptions): UseFetchReturn<...> & Promi...`

<details><summary>Code</summary>

```ts
export function createFetch(config: CreateFetchOptions = {}) {
  const _combination = config.combination || 'chain' as Combination
  const _options = config.options || {}
  const _fetchOptions = config.fetchOptions || {}

  function useFactoryFetch(url: MaybeRefOrGetter<string>, ...args: any[]) {
    const computedUrl = computed(() => {
      const baseUrl = toValue(config.baseUrl)
      const targetUrl = toValue(url)

      return (baseUrl && !isAbsoluteURL(targetUrl))
        ? joinPaths(baseUrl, targetUrl)
        : targetUrl
    })

    let options = _options
    let fetchOptions = _fetchOptions

    // Merge properties into a single object
    if (args.length > 0) {
      if (isFetchOptions(args[0])) {
        options = {
          ...options,
          ...args[0],
          beforeFetch: combineCallbacks(_combination, _options.beforeFetch, args[0].beforeFetch),
          afterFetch: combineCallbacks(_combination, _options.afterFetch, args[0].afterFetch),
          onFetchError: combineCallbacks(_combination, _options.onFetchError, args[0].onFetchError),
        }
      }
      else {
        fetchOptions = {
          ...fetchOptions,
          ...args[0],
          headers: {
            ...(headersToObject(fetchOptions.headers) || {}),
            ...(headersToObject(args[0].headers) || {}),
          },
        }
      }
    }

    if (args.length > 1 && isFetchOptions(args[1])) {
      options = {
        ...options,
        ...args[1],
        beforeFetch: combineCallbacks(_combination, _options.beforeFetch, args[1].beforeFetch),
        afterFetch: combineCallbacks(_combination, _options.afterFetch, args[1].afterFetch),
        onFetchError: combineCallbacks(_combination, _options.onFetchError, args[1].onFetchError),
      }
    }

    return useFetch(computedUrl, fetchOptions, options)
  }

  return useFactoryFetch as typeof useFetch
}
```
</details>

- **Parameters**:
  - `config: CreateFetchOptions`
- **Return Type**: `{ <T>(url: MaybeRefOrGetter<string>): UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>; <T>(url: MaybeRefOrGetter<string>, useFetchOptions: UseFetchOptions): UseFetchReturn<...> & PromiseLike<...>; <T>(url: MaybeRefOrGetter<...>, options: RequestInit, useFetchOptions?: UseFetchOptions): UseFetchReturn<...> & Promi...`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`
  - `isAbsoluteURL`
  - `joinPaths`
  - `isFetchOptions`
  - `combineCallbacks`
  - `headersToObject`
  - `useFetch`
- **Internal Comments**:
```
// Merge properties into a single object
```

### `useFactoryFetch(url: MaybeRefOrGetter<string>, args: any[]): UseFetchReturn<unknown> & PromiseLike<UseFetchReturn<unknown>>`

<details><summary>Code</summary>

```ts
function useFactoryFetch(url: MaybeRefOrGetter<string>, ...args: any[]) {
    const computedUrl = computed(() => {
      const baseUrl = toValue(config.baseUrl)
      const targetUrl = toValue(url)

      return (baseUrl && !isAbsoluteURL(targetUrl))
        ? joinPaths(baseUrl, targetUrl)
        : targetUrl
    })

    let options = _options
    let fetchOptions = _fetchOptions

    // Merge properties into a single object
    if (args.length > 0) {
      if (isFetchOptions(args[0])) {
        options = {
          ...options,
          ...args[0],
          beforeFetch: combineCallbacks(_combination, _options.beforeFetch, args[0].beforeFetch),
          afterFetch: combineCallbacks(_combination, _options.afterFetch, args[0].afterFetch),
          onFetchError: combineCallbacks(_combination, _options.onFetchError, args[0].onFetchError),
        }
      }
      else {
        fetchOptions = {
          ...fetchOptions,
          ...args[0],
          headers: {
            ...(headersToObject(fetchOptions.headers) || {}),
            ...(headersToObject(args[0].headers) || {}),
          },
        }
      }
    }

    if (args.length > 1 && isFetchOptions(args[1])) {
      options = {
        ...options,
        ...args[1],
        beforeFetch: combineCallbacks(_combination, _options.beforeFetch, args[1].beforeFetch),
        afterFetch: combineCallbacks(_combination, _options.afterFetch, args[1].afterFetch),
        onFetchError: combineCallbacks(_combination, _options.onFetchError, args[1].onFetchError),
      }
    }

    return useFetch(computedUrl, fetchOptions, options)
  }
```
</details>

- **Parameters**:
  - `url: MaybeRefOrGetter<string>`
  - `args: any[]`
- **Return Type**: `UseFetchReturn<unknown> & PromiseLike<UseFetchReturn<unknown>>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`
  - `isAbsoluteURL`
  - `joinPaths`
  - `isFetchOptions`
  - `combineCallbacks`
  - `headersToObject`
  - `useFetch`
- **Internal Comments**:
```
// Merge properties into a single object
```

### `useFetch(url: MaybeRefOrGetter<string>): UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>`

<details><summary>Code</summary>

```ts
export function useFetch<T>(url: MaybeRefOrGetter<string>): UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>
```
</details>

- **Parameters**:
  - `url: MaybeRefOrGetter<string>`
- **Return Type**: `UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>`
### `abort(): void`

<details><summary>Code</summary>

```ts
() => {
    if (supportsAbort) {
      controller?.abort()
      controller = new AbortController()
      controller.signal.onabort = () => aborted.value = true
      fetchOptions = {
        ...fetchOptions,
        signal: controller.signal,
      }
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `controller?.abort`
### `loading(isLoading: boolean): void`

<details><summary>Code</summary>

```ts
(isLoading: boolean) => {
    isFetching.value = isLoading
    isFinished.value = !isLoading
  }
```
</details>

- **Parameters**:
  - `isLoading: boolean`
- **Return Type**: `void`
### `execute(throwOnFailed: boolean): Promise<any>`

<details><summary>Code</summary>

```ts
async (throwOnFailed = false) => {
    abort()

    loading(true)
    error.value = null
    statusCode.value = null
    aborted.value = false

    executeCounter += 1
    const currentExecuteCounter = executeCounter

    const defaultFetchOptions: RequestInit = {
      method: config.method,
      headers: {},
    }

    const payload = toValue(config.payload)
    if (payload) {
      const headers = headersToObject(defaultFetchOptions.headers) as Record<string, string>
      // Set the payload to json type only if it's not provided and a literal object or array is provided and the object is not `formData`
      // The only case we can deduce the content type and `fetch` can't
      const proto = Object.getPrototypeOf(payload)
      if (!config.payloadType && payload && (proto === Object.prototype || Array.isArray(proto)) && !(payload instanceof FormData))
        config.payloadType = 'json'

      if (config.payloadType)
        headers['Content-Type'] = payloadMapping[config.payloadType] ?? config.payloadType

      defaultFetchOptions.body = config.payloadType === 'json'
        ? JSON.stringify(payload)
        : payload as BodyInit
    }

    let isCanceled = false
    const context: BeforeFetchContext = {
      url: toValue(url),
      options: {
        ...defaultFetchOptions,
        ...fetchOptions,
      },
      cancel: () => { isCanceled = true },
    }

    if (options.beforeFetch)
      Object.assign(context, await options.beforeFetch(context))

    if (isCanceled || !fetch) {
      loading(false)
      return Promise.resolve(null)
    }

    let responseData: any = null

    if (timer)
      timer.start()

    return fetch(
      context.url,
      {
        ...defaultFetchOptions,
        ...context.options,
        headers: {
          ...headersToObject(defaultFetchOptions.headers),
          ...headersToObject(context.options?.headers),
        },
      },
    )
      .then(async (fetchResponse) => {
        response.value = fetchResponse
        statusCode.value = fetchResponse.status

        responseData = await fetchResponse.clone()[config.type]()

        // see: https://www.tjvantoll.com/2015/09/13/fetch-and-errors/
        if (!fetchResponse.ok) {
          data.value = initialData || null
          throw new Error(fetchResponse.statusText)
        }

        if (options.afterFetch) {
          ({ data: responseData } = await options.afterFetch({
            data: responseData,
            response: fetchResponse,
            context,
            execute,
          }))
        }
        data.value = responseData

        responseEvent.trigger(fetchResponse)
        return fetchResponse
      })
      .catch(async (fetchError) => {
        let errorData = fetchError.message || fetchError.name

        if (options.onFetchError) {
          ({ error: errorData, data: responseData } = await options.onFetchError({
            data: responseData,
            error: fetchError,
            response: response.value,
            context,
            execute,
          }))
        }

        error.value = errorData
        if (options.updateDataOnError)
          data.value = responseData

        errorEvent.trigger(fetchError)
        if (throwOnFailed)
          throw fetchError
        return null
      })
      .finally(() => {
        if (currentExecuteCounter === executeCounter)
          loading(false)
        if (timer)
          timer.stop()
        finallyEvent.trigger(null)
      })
  }
```
</details>

- **Parameters**:
  - `throwOnFailed: boolean`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `abort`
  - `loading`
  - `toValue (from vue)`
  - `headersToObject`
  - `Object.getPrototypeOf`
  - `Array.isArray`
  - `JSON.stringify`
  - `Object.assign`
  - `options.beforeFetch`
  - `Promise.resolve`
  - `timer.start`
  - `fetch(
      context.url,
      {
        ...defaultFetchOptions,
        ...context.options,
        headers: {
          ...headersToObject(defaultFetchOptions.headers),
          ...headersToObject(context.options?.headers),
        },
      },
    )
      .then(async (fetchResponse) => {
        response.value = fetchResponse
        statusCode.value = fetchResponse.status

        responseData = await fetchResponse.clone()[config.type]()

        // see: https://www.tjvantoll.com/2015/09/13/fetch-and-errors/
        if (!fetchResponse.ok) {
          data.value = initialData || null
          throw new Error(fetchResponse.statusText)
        }

        if (options.afterFetch) {
          ({ data: responseData } = await options.afterFetch({
            data: responseData,
            response: fetchResponse,
            context,
            execute,
          }))
        }
        data.value = responseData

        responseEvent.trigger(fetchResponse)
        return fetchResponse
      })
      .catch(async (fetchError) => {
        let errorData = fetchError.message || fetchError.name

        if (options.onFetchError) {
          ({ error: errorData, data: responseData } = await options.onFetchError({
            data: responseData,
            error: fetchError,
            response: response.value,
            context,
            execute,
          }))
        }

        error.value = errorData
        if (options.updateDataOnError)
          data.value = responseData

        errorEvent.trigger(fetchError)
        if (throwOnFailed)
          throw fetchError
        return null
      })
      .finally`
  - `timer.stop`
  - `finallyEvent.trigger`
- **Internal Comments**:
```
// Set the payload to json type only if it's not provided and a literal object or array is provided and the object is not `formData` (x2)
// The only case we can deduce the content type and `fetch` can't (x2)
// see: https://www.tjvantoll.com/2015/09/13/fetch-and-errors/
```

### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => { isCanceled = true }
```
</details>

- **Return Type**: `void`
### `setMethod(method: HttpMethod): (payload?: unknown, payloadType?: string) => any`

<details><summary>Code</summary>

```ts
function setMethod(method: HttpMethod) {
    return (payload?: unknown, payloadType?: string) => {
      if (!isFetching.value) {
        config.method = method
        config.payload = payload
        config.payloadType = payloadType

        // watch for payload changes
        if (isRef(config.payload)) {
          watch(
            [
              refetch,
              toRef(config.payload),
            ],
            ([refetch]) => refetch && execute(),
            { deep: true },
          )
        }

        return {
          ...shell,
          then(onFulfilled: any, onRejected: any) {
            return waitUntilFinished()
              .then(onFulfilled, onRejected)
          },
        } as any
      }
      return undefined
    }
  }
```
</details>

- **Parameters**:
  - `method: HttpMethod`
- **Return Type**: `(payload?: unknown, payloadType?: string) => any`
- **Calls**:
  - `isRef (from vue)`
  - `watch (from vue)`
  - `toRef (from @vueuse/shared)`
  - `execute`
  - `waitUntilFinished()
              .then`
- **Internal Comments**:
```
// watch for payload changes
```

### `waitUntilFinished(): Promise<UseFetchReturn<T>>`

<details><summary>Code</summary>

```ts
function waitUntilFinished() {
    return new Promise<UseFetchReturn<T>>((resolve, reject) => {
      until(isFinished).toBe(true).then(() => resolve(shell)).catch(reject)
    })
  }
```
</details>

- **Return Type**: `Promise<UseFetchReturn<T>>`
- **Calls**:
  - `until(isFinished).toBe(true).then(() => resolve(shell)).catch`
### `setType(type: DataType): () => any`

<details><summary>Code</summary>

```ts
function setType(type: DataType) {
    return () => {
      if (!isFetching.value) {
        config.type = type
        return {
          ...shell,
          then(onFulfilled: any, onRejected: any) {
            return waitUntilFinished()
              .then(onFulfilled, onRejected)
          },
        } as any
      }
      return undefined
    }
  }
```
</details>

- **Parameters**:
  - `type: DataType`
- **Return Type**: `() => any`
- **Calls**:
  - `waitUntilFinished()
              .then`
### `joinPaths(start: string, end: string): string`

<details><summary>Code</summary>

```ts
function joinPaths(start: string, end: string): string {
  if (!start.endsWith('/') && !end.startsWith('/')) {
    return `${start}/${end}`
  }

  if (start.endsWith('/') && end.startsWith('/')) {
    return `${start.slice(0, -1)}${end}`
  }

  return `${start}${end}`
}
```
</details>

- **Parameters**:
  - `start: string`
  - `end: string`
- **Return Type**: `string`
- **Calls**:
  - `start.endsWith`
  - `end.startsWith`
  - `start.slice`

---

## Interfaces

### `UseFetchReturn<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseFetchReturn<T> {
  /**
   * Indicates if the fetch request has finished
   */
  isFinished: Readonly<ShallowRef<boolean>>

  /**
   * The statusCode of the HTTP fetch response
   */
  statusCode: ShallowRef<number | null>

  /**
   * The raw response of the fetch response
   */
  response: ShallowRef<Response | null>

  /**
   * Any fetch errors that may have occurred
   */
  error: ShallowRef<any>

  /**
   * The fetch response body on success, may either be JSON or text
   */
  data: ShallowRef<T | null>

  /**
   * Indicates if the request is currently being fetched.
   */
  isFetching: Readonly<ShallowRef<boolean>>

  /**
   * Indicates if the fetch request is able to be aborted
   */
  canAbort: ComputedRef<boolean>

  /**
   * Indicates if the fetch request was aborted
   */
  aborted: ShallowRef<boolean>

  /**
   * Abort the fetch request
   */
  abort: Fn

  /**
   * Manually call the fetch
   * (default not throwing error)
   */
  execute: (throwOnFailed?: boolean) => Promise<any>

  /**
   * Fires after the fetch request has finished
   */
  onFetchResponse: EventHookOn<Response>

  /**
   * Fires after a fetch request error
   */
  onFetchError: EventHookOn

  /**
   * Fires after a fetch has completed
   */
  onFetchFinally: EventHookOn

  // methods
  get: () => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>
  post: (payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>
  put: (payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>
  delete: (payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>
  patch: (payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>
  head: (payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>
  options: (payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>

  // type
  json: <JSON = any>() => UseFetchReturn<JSON> & PromiseLike<UseFetchReturn<JSON>>
  text: () => UseFetchReturn<string> & PromiseLike<UseFetchReturn<string>>
  blob: () => UseFetchReturn<Blob> & PromiseLike<UseFetchReturn<Blob>>
  arrayBuffer: () => UseFetchReturn<ArrayBuffer> & PromiseLike<UseFetchReturn<ArrayBuffer>>
  formData: () => UseFetchReturn<FormData> & PromiseLike<UseFetchReturn<FormData>>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isFinished` | `Readonly<ShallowRef<boolean>>` | ✗ |  |
| `statusCode` | `ShallowRef<number | null>` | ✗ |  |
| `response` | `ShallowRef<Response | null>` | ✗ |  |
| `error` | `ShallowRef<any>` | ✗ |  |
| `data` | `ShallowRef<T | null>` | ✗ |  |
| `isFetching` | `Readonly<ShallowRef<boolean>>` | ✗ |  |
| `canAbort` | `ComputedRef<boolean>` | ✗ |  |
| `aborted` | `ShallowRef<boolean>` | ✗ |  |
| `abort` | `Fn` | ✗ |  |
| `execute` | `(throwOnFailed?: boolean) => Promise<any>` | ✗ |  |
| `onFetchResponse` | `EventHookOn<Response>` | ✗ |  |
| `onFetchError` | `EventHookOn` | ✗ |  |
| `onFetchFinally` | `EventHookOn` | ✗ |  |
| `get` | `() => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>` | ✗ |  |
| `post` | `(payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>` | ✗ |  |
| `put` | `(payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>` | ✗ |  |
| `delete` | `(payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>` | ✗ |  |
| `patch` | `(payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>` | ✗ |  |
| `head` | `(payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>` | ✗ |  |
| `options` | `(payload?: MaybeRefOrGetter<unknown>, type?: string) => UseFetchReturn<T> & PromiseLike<UseFetchReturn<T>>` | ✗ |  |
| `json` | `<JSON = any>() => UseFetchReturn<JSON> & PromiseLike<UseFetchReturn<JSON>>` | ✗ |  |
| `text` | `() => UseFetchReturn<string> & PromiseLike<UseFetchReturn<string>>` | ✗ |  |
| `blob` | `() => UseFetchReturn<Blob> & PromiseLike<UseFetchReturn<Blob>>` | ✗ |  |
| `arrayBuffer` | `() => UseFetchReturn<ArrayBuffer> & PromiseLike<UseFetchReturn<ArrayBuffer>>` | ✗ |  |
| `formData` | `() => UseFetchReturn<FormData> & PromiseLike<UseFetchReturn<FormData>>` | ✗ |  |

### `BeforeFetchContext`

<details><summary>Interface Code</summary>

```ts
export interface BeforeFetchContext {
  /**
   * The computed url of the current request
   */
  url: string

  /**
   * The request options of the current request
   */
  options: RequestInit

  /**
   * Cancels the current request
   */
  cancel: Fn
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `url` | `string` | ✗ |  |
| `options` | `RequestInit` | ✗ |  |
| `cancel` | `Fn` | ✗ |  |

### `AfterFetchContext<T = any>`

<details><summary>Interface Code</summary>

```ts
export interface AfterFetchContext<T = any> {
  response: Response

  data: T | null

  context: BeforeFetchContext

  execute: (throwOnFailed?: boolean) => Promise<any>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `response` | `Response` | ✗ |  |
| `data` | `T | null` | ✗ |  |
| `context` | `BeforeFetchContext` | ✗ |  |
| `execute` | `(throwOnFailed?: boolean) => Promise<any>` | ✗ |  |

### `OnFetchErrorContext<T = any, E = any>`

<details><summary>Interface Code</summary>

```ts
export interface OnFetchErrorContext<T = any, E = any> {
  error: E

  data: T | null

  response: Response | null

  context: BeforeFetchContext

  execute: (throwOnFailed?: boolean) => Promise<any>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `error` | `E` | ✗ |  |
| `data` | `T | null` | ✗ |  |
| `response` | `Response | null` | ✗ |  |
| `context` | `BeforeFetchContext` | ✗ |  |
| `execute` | `(throwOnFailed?: boolean) => Promise<any>` | ✗ |  |

### `UseFetchOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFetchOptions {
  /**
   * Fetch function
   */
  fetch?: typeof window.fetch

  /**
   * Will automatically run fetch when `useFetch` is used
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Will automatically refetch when:
   * - the URL is changed if the URL is a ref
   * - the payload is changed if the payload is a ref
   *
   * @default false
   */
  refetch?: MaybeRefOrGetter<boolean>

  /**
   * Initial data before the request finished
   *
   * @default null
   */
  initialData?: any

  /**
   * Timeout for abort request after number of millisecond
   * `0` means use browser default
   *
   * @default 0
   */
  timeout?: number

  /**
   * Allow update the `data` ref when fetch error whenever provided, or mutated in the `onFetchError` callback
   *
   * @default false
   */
  updateDataOnError?: boolean

  /**
   * Will run immediately before the fetch request is dispatched
   */
  beforeFetch?: (ctx: BeforeFetchContext) => Promise<Partial<BeforeFetchContext> | void> | Partial<BeforeFetchContext> | void

  /**
   * Will run immediately after the fetch request is returned.
   * Runs after any 2xx response
   */
  afterFetch?: (ctx: AfterFetchContext) => Promise<Partial<AfterFetchContext>> | Partial<AfterFetchContext>

  /**
   * Will run immediately after the fetch request is returned.
   * Runs after any 4xx and 5xx response
   */
  onFetchError?: (ctx: OnFetchErrorContext) => Promise<Partial<OnFetchErrorContext>> | Partial<OnFetchErrorContext>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `fetch` | `typeof window.fetch` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `refetch` | `MaybeRefOrGetter<boolean>` | ✓ |  |
| `initialData` | `any` | ✓ |  |
| `timeout` | `number` | ✓ |  |
| `updateDataOnError` | `boolean` | ✓ |  |
| `beforeFetch` | `(ctx: BeforeFetchContext) => Promise<Partial<BeforeFetchContext> | void> | Partial<BeforeFetchContext> | void` | ✓ |  |
| `afterFetch` | `(ctx: AfterFetchContext) => Promise<Partial<AfterFetchContext>> | Partial<AfterFetchContext>` | ✓ |  |
| `onFetchError` | `(ctx: OnFetchErrorContext) => Promise<Partial<OnFetchErrorContext>> | Partial<OnFetchErrorContext>` | ✓ |  |

### `CreateFetchOptions`

<details><summary>Interface Code</summary>

```ts
export interface CreateFetchOptions {
  /**
   * The base URL that will be prefixed to all urls unless urls are absolute
   */
  baseUrl?: MaybeRefOrGetter<string>

  /**
   * Determine the inherit behavior for beforeFetch, afterFetch, onFetchError
   * @default 'chain'
   */
  combination?: Combination

  /**
   * Default Options for the useFetch function
   */
  options?: UseFetchOptions

  /**
   * Options for the fetch request
   */
  fetchOptions?: RequestInit
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `baseUrl` | `MaybeRefOrGetter<string>` | ✓ |  |
| `combination` | `Combination` | ✓ |  |
| `options` | `UseFetchOptions` | ✓ |  |
| `fetchOptions` | `RequestInit` | ✓ |  |

### `InternalConfig`

<details><summary>Interface Code</summary>

```ts
interface InternalConfig {
    method: HttpMethod
    type: DataType
    payload: unknown
    payloadType?: string
  }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `method` | `HttpMethod` | ✗ |  |
| `type` | `DataType` | ✗ |  |
| `payload` | `unknown` | ✗ |  |
| `payloadType` | `string` | ✓ |  |


---

## Type Aliases

### `DataType`

```ts
type DataType = 'text' | 'json' | 'blob' | 'arrayBuffer' | 'formData';
```

### `HttpMethod`

```ts
type HttpMethod = 'GET' | 'POST' | 'PUT' | 'DELETE' | 'PATCH' | 'HEAD' | 'OPTIONS';
```

### `Combination`

```ts
type Combination = 'overwrite' | 'chain';
```


---