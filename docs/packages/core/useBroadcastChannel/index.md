[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useBroadcastChannel/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `tryOnMounted` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `listenerOptions` | `{ passive: boolean; }` | const | `{
        passive: true,
      }` | ✗ |


---

## Functions

### `useBroadcastChannel(options: UseBroadcastChannelOptions): UseBroadcastChannelReturn<D, P>`

<details><summary>Code</summary>

```ts
export function useBroadcastChannel<D, P>(options: UseBroadcastChannelOptions): UseBroadcastChannelReturn<D, P> {
  const {
    name,
    window = defaultWindow,
  } = options

  const isSupported = useSupported(() => window && 'BroadcastChannel' in window)
  const isClosed = shallowRef(false)

  const channel = deepRef<BroadcastChannel | undefined>()
  const data = deepRef()
  const error = shallowRef<Event | null>(null)

  const post = (data: unknown) => {
    if (channel.value)
      channel.value.postMessage(data)
  }

  const close = () => {
    if (channel.value)
      channel.value.close()
    isClosed.value = true
  }

  if (isSupported.value) {
    tryOnMounted(() => {
      error.value = null
      channel.value = new BroadcastChannel(name)

      const listenerOptions = {
        passive: true,
      }

      useEventListener(channel, 'message', (e: MessageEvent) => {
        data.value = e.data
      }, listenerOptions)

      useEventListener(channel, 'messageerror', (e: MessageEvent) => {
        error.value = e
      }, listenerOptions)

      useEventListener(channel, 'close', () => {
        isClosed.value = true
      }, listenerOptions)
    })
  }

  tryOnScopeDispose(() => {
    close()
  })

  return {
    isSupported,
    channel,
    data,
    post,
    close,
    error,
    isClosed,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive BroadcastChannel
 *
 * @see https://vueuse.org/useBroadcastChannel
 * @see https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel
 * @param options
 *
 */
```

- **Parameters**:
  - `options: UseBroadcastChannelOptions`
- **Return Type**: `UseBroadcastChannelReturn<D, P>`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `channel.value.postMessage`
  - `channel.value.close`
  - `tryOnMounted (from @vueuse/shared)`
  - `useEventListener (from ../useEventListener)`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `close`
### `post(data: unknown): void`

<details><summary>Code</summary>

```ts
(data: unknown) => {
    if (channel.value)
      channel.value.postMessage(data)
  }
```
</details>

- **Parameters**:
  - `data: unknown`
- **Return Type**: `void`
- **Calls**:
  - `channel.value.postMessage`
### `close(): void`

<details><summary>Code</summary>

```ts
() => {
    if (channel.value)
      channel.value.close()
    isClosed.value = true
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `channel.value.close`

---

## Interfaces

### `UseBroadcastChannelOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseBroadcastChannelOptions extends ConfigurableWindow {
  /**
   * The name of the channel.
   */
  name: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `name` | `string` | ✗ |  |

### `UseBroadcastChannelReturn<D, P>`

<details><summary>Interface Code</summary>

```ts
export interface UseBroadcastChannelReturn<D, P> {
  isSupported: ComputedRef<boolean>
  channel: Ref<BroadcastChannel | undefined>
  data: Ref<D>
  post: (data: P) => void
  close: () => void
  error: ShallowRef<Event | null>
  isClosed: ShallowRef<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `channel` | `Ref<BroadcastChannel | undefined>` | ✗ |  |
| `data` | `Ref<D>` | ✗ |  |
| `post` | `(data: P) => void` | ✗ |  |
| `close` | `() => void` | ✗ |  |
| `error` | `ShallowRef<Event | null>` | ✗ |  |
| `isClosed` | `ShallowRef<boolean>` | ✗ |  |


---