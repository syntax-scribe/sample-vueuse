[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 13
- **Interfaces**: 2
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/useEventListener/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Arrayable` | `@vueuse/shared` |
| `Fn` | `@vueuse/shared` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `isObject` | `@vueuse/shared` |
| `toArray` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `watchImmediate` | `@vueuse/shared` |
| `computed` | `vue` |
| `toValue` | `vue` |
| `unref` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |


---

## Functions

### `useEventListener(event: MaybeRefOrGetter<Arrayable<E>>, listener: MaybeRef<Arrayable<(this: Window, ev: WindowEventMap[E]) => any>>, options: MaybeRefOrGetter<boolean | AddEventListenerOptions>): Fn`

<details><summary>Code</summary>

```ts
export function useEventListener<E extends keyof WindowEventMap>(
  event: MaybeRefOrGetter<Arrayable<E>>,
  listener: MaybeRef<Arrayable<(this: Window, ev: WindowEventMap[E]) => any>>,
  options?: MaybeRefOrGetter<boolean | AddEventListenerOptions>
): Fn
```
</details>

- **JSDoc**:
```ts
/**
 * Register using addEventListener on mounted, and removeEventListener automatically on unmounted.
 *
 * Overload 1: Omitted Window target
 *
 * @see https://vueuse.org/useEventListener
 * @param event
 * @param listener
 * @param options
 */
```

- **Parameters**:
  - `event: MaybeRefOrGetter<Arrayable<E>>`
  - `listener: MaybeRef<Arrayable<(this: Window, ev: WindowEventMap[E]) => any>>`
  - `options: MaybeRefOrGetter<boolean | AddEventListenerOptions>`
- **Return Type**: `Fn`
### `cleanup(): void`

<details><summary>Code</summary>

```ts
() => {
    cleanups.forEach(fn => fn())
    cleanups.length = 0
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `cleanups.forEach`
  - `fn`
### `register(el: EventTarget, event: string, listener: any, options: boolean | AddEventListenerOptions | undefined): () => void`

<details><summary>Code</summary>

```ts
(
    el: EventTarget,
    event: string,
    listener: any,
    options: boolean | AddEventListenerOptions | undefined,
  ) => {
    el.addEventListener(event, listener, options)
    return () => el.removeEventListener(event, listener, options)
  }
```
</details>

- **Parameters**:
  - `el: EventTarget`
  - `event: string`
  - `listener: any`
  - `options: boolean | AddEventListenerOptions | undefined`
- **Return Type**: `() => void`
- **Calls**:
  - `el.addEventListener`
  - `el.removeEventListener`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    stopWatch()
    cleanup()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stopWatch`
  - `cleanup`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `InferEventTarget<Events>`

<details><summary>Interface Code</summary>

```ts
interface InferEventTarget<Events> {
  addEventListener: (event: Events, fn?: any, options?: any) => any
  removeEventListener: (event: Events, fn?: any, options?: any) => any
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `addEventListener` | `(event: Events, fn?: any, options?: any) => any` | ✗ |  |
| `removeEventListener` | `(event: Events, fn?: any, options?: any) => any` | ✗ |  |

### `GeneralEventListener<E = Event>`

<details><summary>Interface Code</summary>

```ts
export interface GeneralEventListener<E = Event> {
  (evt: E): void
}
```
</details>


---

## Type Aliases

### `WindowEventName`

```ts
type WindowEventName = keyof WindowEventMap;
```

### `DocumentEventName`

```ts
type DocumentEventName = keyof DocumentEventMap;
```


---