[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 8
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 2
- **Type Aliases**: 3

## 🛠️ File Location:
📂 **`packages/core/useEventBus/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `getCurrentScope` | `vue` |
| `events` | `./internal` |


---

## Functions

### `useEventBus(key: EventBusIdentifier<T>): UseEventBusReturn<T, P>`

<details><summary>Code</summary>

```ts
export function useEventBus<T = unknown, P = any>(key: EventBusIdentifier<T>): UseEventBusReturn<T, P> {
  const scope = getCurrentScope()
  function on(listener: EventBusListener<T, P>) {
    const listeners = (events.get(key) || new Set())
    listeners.add(listener)
    events.set(key, listeners)

    const _off = () => off(listener)
    // auto unsubscribe when scope get disposed
    // @ts-expect-error vue3 and vue2 mis-align
    scope?.cleanups?.push(_off)
    return _off
  }

  function once(listener: EventBusListener<T, P>) {
    function _listener(...args: any[]) {
      off(_listener)
      // @ts-expect-error cast
      listener(...args)
    }
    return on(_listener)
  }

  function off(listener: EventBusListener<T>): void {
    const listeners = events.get(key)
    if (!listeners)
      return

    listeners.delete(listener)

    if (!listeners.size)
      reset()
  }

  function reset() {
    events.delete(key)
  }

  function emit(event?: T, payload?: P) {
    events.get(key)?.forEach(v => v(event, payload))
  }

  return { on, once, off, emit, reset }
}
```
</details>

- **Parameters**:
  - `key: EventBusIdentifier<T>`
- **Return Type**: `UseEventBusReturn<T, P>`
- **Calls**:
  - `getCurrentScope (from vue)`
  - `events.get`
  - `listeners.add`
  - `events.set`
  - `off`
  - `scope?.cleanups?.push`
  - `listener`
  - `on`
  - `listeners.delete`
  - `reset`
  - `events.delete`
  - `events.get(key)?.forEach`
  - `v`
- **Internal Comments**:
```
// auto unsubscribe when scope get disposed (x5)
// @ts-expect-error vue3 and vue2 mis-align (x5)
// @ts-expect-error cast (x3)
```

### `on(listener: EventBusListener<T, P>): () => void`

<details><summary>Code</summary>

```ts
function on(listener: EventBusListener<T, P>) {
    const listeners = (events.get(key) || new Set())
    listeners.add(listener)
    events.set(key, listeners)

    const _off = () => off(listener)
    // auto unsubscribe when scope get disposed
    // @ts-expect-error vue3 and vue2 mis-align
    scope?.cleanups?.push(_off)
    return _off
  }
```
</details>

- **Parameters**:
  - `listener: EventBusListener<T, P>`
- **Return Type**: `() => void`
- **Calls**:
  - `events.get`
  - `listeners.add`
  - `events.set`
  - `off`
  - `scope?.cleanups?.push`
- **Internal Comments**:
```
// auto unsubscribe when scope get disposed (x5)
// @ts-expect-error vue3 and vue2 mis-align (x5)
```

### `_off(): void`

<details><summary>Code</summary>

```ts
() => off(listener)
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `off`
### `once(listener: EventBusListener<T, P>): () => void`

<details><summary>Code</summary>

```ts
function once(listener: EventBusListener<T, P>) {
    function _listener(...args: any[]) {
      off(_listener)
      // @ts-expect-error cast
      listener(...args)
    }
    return on(_listener)
  }
```
</details>

- **Parameters**:
  - `listener: EventBusListener<T, P>`
- **Return Type**: `() => void`
- **Calls**:
  - `off`
  - `listener`
  - `on`
- **Internal Comments**:
```
// @ts-expect-error cast (x3)
```

### `_listener(args: any[]): void`

<details><summary>Code</summary>

```ts
function _listener(...args: any[]) {
      off(_listener)
      // @ts-expect-error cast
      listener(...args)
    }
```
</details>

- **Parameters**:
  - `args: any[]`
- **Return Type**: `void`
- **Calls**:
  - `off`
  - `listener`
- **Internal Comments**:
```
// @ts-expect-error cast (x3)
```

### `off(listener: EventBusListener<T>): void`

<details><summary>Code</summary>

```ts
function off(listener: EventBusListener<T>): void {
    const listeners = events.get(key)
    if (!listeners)
      return

    listeners.delete(listener)

    if (!listeners.size)
      reset()
  }
```
</details>

- **Parameters**:
  - `listener: EventBusListener<T>`
- **Return Type**: `void`
- **Calls**:
  - `events.get`
  - `listeners.delete`
  - `reset`
### `reset(): void`

<details><summary>Code</summary>

```ts
function reset() {
    events.delete(key)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `events.delete`
### `emit(event: T, payload: P): void`

<details><summary>Code</summary>

```ts
function emit(event?: T, payload?: P) {
    events.get(key)?.forEach(v => v(event, payload))
  }
```
</details>

- **Parameters**:
  - `event: T`
  - `payload: P`
- **Return Type**: `void`
- **Calls**:
  - `events.get(key)?.forEach`
  - `v`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `EventBusKey<T>`

<details><summary>Interface Code</summary>

```ts
export interface EventBusKey<T> extends Symbol { }
```
</details>

### `UseEventBusReturn<T, P>`

<details><summary>Interface Code</summary>

```ts
export interface UseEventBusReturn<T, P> {
  /**
   * Subscribe to an event. When calling emit, the listeners will execute.
   * @param listener watch listener.
   * @returns a stop function to remove the current callback.
   */
  on: (listener: EventBusListener<T, P>) => Fn
  /**
   * Similar to `on`, but only fires once
   * @param listener watch listener.
   * @returns a stop function to remove the current callback.
   */
  once: (listener: EventBusListener<T, P>) => Fn
  /**
   * Emit an event, the corresponding event listeners will execute.
   * @param event data sent.
   */
  emit: (event?: T, payload?: P) => void
  /**
   * Remove the corresponding listener.
   * @param listener watch listener.
   */
  off: (listener: EventBusListener<T>) => void
  /**
   * Clear all events
   */
  reset: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `on` | `(listener: EventBusListener<T, P>) => Fn` | ✗ |  |
| `once` | `(listener: EventBusListener<T, P>) => Fn` | ✗ |  |
| `emit` | `(event?: T, payload?: P) => void` | ✗ |  |
| `off` | `(listener: EventBusListener<T>) => void` | ✗ |  |
| `reset` | `() => void` | ✗ |  |


---

## Type Aliases

### `EventBusListener<T = unknown = unknown, P = any = any>`

```ts
type EventBusListener<T = unknown = unknown, P = any = any> = (event: T, payload?: P) => void;
```

### `EventBusEvents<T, P = any = any>`

```ts
type EventBusEvents<T, P = any = any> = Set<EventBusListener<T, P>>;
```

### `EventBusIdentifier<T = unknown = unknown>`

```ts
type EventBusIdentifier<T = unknown = unknown> = EventBusKey<T> | string | number;
```


---