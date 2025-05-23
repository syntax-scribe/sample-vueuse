[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 5
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useEventSource/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `isClient` | `@vueuse/shared` |
| `toRef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `resolveNestedOptions(options: T | true): T`

<details><summary>Code</summary>

```ts
function resolveNestedOptions<T>(options: T | true): T {
  if (options === true)
    return {} as T
  return options
}
```
</details>

- **Parameters**:
  - `options: T | true`
- **Return Type**: `T`
### `useEventSource(url: MaybeRefOrGetter<string | URL | undefined>, events: Events, options: UseEventSourceOptions): UseEventSourceReturn<Events, Data>`

<details><summary>Code</summary>

```ts
export function useEventSource<Events extends string[], Data = any>(
  url: MaybeRefOrGetter<string | URL | undefined>,
  events: Events = [] as unknown as Events,
  options: UseEventSourceOptions = {},
): UseEventSourceReturn<Events, Data> {
  const event: ShallowRef<string | null> = shallowRef(null)
  const data: ShallowRef<Data | null> = shallowRef(null)
  const status = shallowRef<EventSourceStatus>('CONNECTING')
  const eventSource = deepRef<EventSource | null>(null)
  const error = shallowRef<Event | null>(null)
  const urlRef = toRef(url)
  const lastEventId = shallowRef<string | null>(null)

  let explicitlyClosed = false
  let retried = 0

  const {
    withCredentials = false,
    immediate = true,
    autoConnect = true,
    autoReconnect,
  } = options

  const close = () => {
    if (isClient && eventSource.value) {
      eventSource.value.close()
      eventSource.value = null
      status.value = 'CLOSED'
      explicitlyClosed = true
    }
  }

  const _init = () => {
    if (explicitlyClosed || typeof urlRef.value === 'undefined')
      return

    const es = new EventSource(urlRef.value, { withCredentials })

    status.value = 'CONNECTING'

    eventSource.value = es

    es.onopen = () => {
      status.value = 'OPEN'
      error.value = null
    }

    es.onerror = (e) => {
      status.value = 'CLOSED'
      error.value = e

      // only reconnect if EventSource isn't reconnecting by itself
      // this is the case when the connection is closed (readyState is 2)
      if (es.readyState === 2 && !explicitlyClosed && autoReconnect) {
        es.close()
        const {
          retries = -1,
          delay = 1000,
          onFailed,
        } = resolveNestedOptions(autoReconnect)
        retried += 1

        if (typeof retries === 'number' && (retries < 0 || retried < retries))
          setTimeout(_init, delay)
        else if (typeof retries === 'function' && retries())
          setTimeout(_init, delay)
        else
          onFailed?.()
      }
    }

    es.onmessage = (e: MessageEvent) => {
      event.value = null
      data.value = e.data
      lastEventId.value = e.lastEventId
    }

    for (const event_name of events) {
      useEventListener(es, event_name, (e: Event & { data?: Data }) => {
        event.value = event_name
        data.value = e.data || null
      }, { passive: true })
    }
  }

  const open = () => {
    if (!isClient)
      return
    close()
    explicitlyClosed = false
    retried = 0
    _init()
  }

  if (immediate)
    open()

  if (autoConnect)
    watch(urlRef, open)

  tryOnScopeDispose(close)

  return {
    eventSource,
    event,
    data,
    status,
    error,
    open,
    close,
    lastEventId,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive wrapper for EventSource.
 *
 * @see https://vueuse.org/useEventSource
 * @see https://developer.mozilla.org/en-US/docs/Web/API/EventSource/EventSource EventSource
 * @param url
 * @param events
 * @param options
 */
```

- **Parameters**:
  - `url: MaybeRefOrGetter<string | URL | undefined>`
  - `events: Events`
  - `options: UseEventSourceOptions`
- **Return Type**: `UseEventSourceReturn<Events, Data>`
- **Calls**:
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `toRef (from @vueuse/shared)`
  - `eventSource.value.close`
  - `es.close`
  - `resolveNestedOptions`
  - `setTimeout`
  - `retries`
  - `onFailed`
  - `useEventListener (from ../useEventListener)`
  - `close`
  - `_init`
  - `open`
  - `watch (from vue)`
  - `tryOnScopeDispose (from @vueuse/shared)`
- **Internal Comments**:
```
// only reconnect if EventSource isn't reconnecting by itself
// this is the case when the connection is closed (readyState is 2)
```

### `close(): void`

<details><summary>Code</summary>

```ts
() => {
    if (isClient && eventSource.value) {
      eventSource.value.close()
      eventSource.value = null
      status.value = 'CLOSED'
      explicitlyClosed = true
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `eventSource.value.close`
### `_init(): void`

<details><summary>Code</summary>

```ts
() => {
    if (explicitlyClosed || typeof urlRef.value === 'undefined')
      return

    const es = new EventSource(urlRef.value, { withCredentials })

    status.value = 'CONNECTING'

    eventSource.value = es

    es.onopen = () => {
      status.value = 'OPEN'
      error.value = null
    }

    es.onerror = (e) => {
      status.value = 'CLOSED'
      error.value = e

      // only reconnect if EventSource isn't reconnecting by itself
      // this is the case when the connection is closed (readyState is 2)
      if (es.readyState === 2 && !explicitlyClosed && autoReconnect) {
        es.close()
        const {
          retries = -1,
          delay = 1000,
          onFailed,
        } = resolveNestedOptions(autoReconnect)
        retried += 1

        if (typeof retries === 'number' && (retries < 0 || retried < retries))
          setTimeout(_init, delay)
        else if (typeof retries === 'function' && retries())
          setTimeout(_init, delay)
        else
          onFailed?.()
      }
    }

    es.onmessage = (e: MessageEvent) => {
      event.value = null
      data.value = e.data
      lastEventId.value = e.lastEventId
    }

    for (const event_name of events) {
      useEventListener(es, event_name, (e: Event & { data?: Data }) => {
        event.value = event_name
        data.value = e.data || null
      }, { passive: true })
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `es.close`
  - `resolveNestedOptions`
  - `setTimeout`
  - `retries`
  - `onFailed`
  - `useEventListener (from ../useEventListener)`
- **Internal Comments**:
```
// only reconnect if EventSource isn't reconnecting by itself
// this is the case when the connection is closed (readyState is 2)
```

### `open(): void`

<details><summary>Code</summary>

```ts
() => {
    if (!isClient)
      return
    close()
    explicitlyClosed = false
    retried = 0
    _init()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `close`
  - `_init`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseEventSourceOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseEventSourceOptions extends EventSourceInit {
  /**
   * Enabled auto reconnect
   *
   * @default false
   */
  autoReconnect?: boolean | {
    /**
     * Maximum retry times.
     *
     * Or you can pass a predicate function (which returns true if you want to retry).
     *
     * @default -1
     */
    retries?: number | (() => boolean)

    /**
     * Delay for reconnect, in milliseconds
     *
     * @default 1000
     */
    delay?: number

    /**
     * On maximum retry times reached.
     */
    onFailed?: Fn
  }

  /**
   * Immediately open the connection when calling this composable
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Automatically connect to the websocket when URL changes
   *
   * @default true
   */
  autoConnect?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `autoReconnect` | `boolean | {
    /**
     * Maximum retry times.
     *
     * Or you can pass a predicate function (which returns true if you want to retry).
     *
     * @default -1
     */
    retries?: number | (() => boolean)

    /**
     * Delay for reconnect, in milliseconds
     *
     * @default 1000
     */
    delay?: number

    /**
     * On maximum retry times reached.
     */
    onFailed?: Fn
  }` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `autoConnect` | `boolean` | ✓ |  |

### `UseEventSourceReturn<Events extends string[], Data = any>`

<details><summary>Interface Code</summary>

```ts
export interface UseEventSourceReturn<Events extends string[], Data = any> {
  /**
   * Reference to the latest data received via the EventSource,
   * can be watched to respond to incoming messages
   */
  data: ShallowRef<Data | null>

  /**
   * The current state of the connection, can be only one of:
   * 'CONNECTING', 'OPEN' 'CLOSED'
   */
  status: ShallowRef<EventSourceStatus>

  /**
   * The latest named event
   */
  event: ShallowRef<Events[number] | null>

  /**
   * The current error
   */
  error: ShallowRef<Event | null>

  /**
   * Closes the EventSource connection gracefully.
   */
  close: EventSource['close']

  /**
   * Reopen the EventSource connection.
   * If there the current one is active, will close it before opening a new one.
   */
  open: Fn

  /**
   * Reference to the current EventSource instance.
   */
  eventSource: Ref<EventSource | null>
  /**
   * The last event ID string, for server-sent events.
   * @see https://developer.mozilla.org/en-US/docs/Web/API/MessageEvent/lastEventId
   */
  lastEventId: ShallowRef<string | null>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `data` | `ShallowRef<Data | null>` | ✗ |  |
| `status` | `ShallowRef<EventSourceStatus>` | ✗ |  |
| `event` | `ShallowRef<Events[number] | null>` | ✗ |  |
| `error` | `ShallowRef<Event | null>` | ✗ |  |
| `close` | `EventSource['close']` | ✗ |  |
| `open` | `Fn` | ✗ |  |
| `eventSource` | `Ref<EventSource | null>` | ✗ |  |
| `lastEventId` | `ShallowRef<string | null>` | ✗ |  |


---

## Type Aliases

### `EventSourceStatus`

```ts
type EventSourceStatus = 'CONNECTING' | 'OPEN' | 'CLOSED';
```


---