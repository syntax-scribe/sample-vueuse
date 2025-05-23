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
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useDisplayMedia/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useDisplayMedia(options: UseDisplayMediaOptions): { isSupported: any; stream: any; start: () => Promise<any>; stop: () => void; enabled: any; }`

<details><summary>Code</summary>

```ts
export function useDisplayMedia(options: UseDisplayMediaOptions = {}) {
  const enabled = shallowRef(options.enabled ?? false)
  const video = options.video
  const audio = options.audio
  const { navigator = defaultNavigator } = options
  const isSupported = useSupported(() => navigator?.mediaDevices?.getDisplayMedia)

  const constraint: MediaStreamConstraints = { audio, video }

  const stream = shallowRef<MediaStream | undefined>()

  async function _start() {
    if (!isSupported.value || stream.value)
      return
    stream.value = await navigator!.mediaDevices.getDisplayMedia(constraint)
    stream.value?.getTracks().forEach(t => useEventListener(t, 'ended', stop, { passive: true }))
    return stream.value
  }

  async function _stop() {
    stream.value?.getTracks().forEach(t => t.stop())
    stream.value = undefined
  }

  function stop() {
    _stop()
    enabled.value = false
  }

  async function start() {
    await _start()
    if (stream.value)
      enabled.value = true
    return stream.value
  }

  watch(
    enabled,
    (v) => {
      if (v)
        _start()
      else
        _stop()
    },
    { immediate: true },
  )

  return {
    isSupported,
    stream,
    start,
    stop,
    enabled,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `mediaDevices.getDisplayMedia` streaming
 *
 * @see https://vueuse.org/useDisplayMedia
 * @param options
 */
```

- **Parameters**:
  - `options: UseDisplayMediaOptions`
- **Return Type**: `{ isSupported: any; stream: any; start: () => Promise<any>; stop: () => void; enabled: any; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `useSupported (from ../useSupported)`
  - `navigator!.mediaDevices.getDisplayMedia`
  - `stream.value?.getTracks().forEach`
  - `useEventListener (from ../useEventListener)`
  - `t.stop`
  - `_stop`
  - `_start`
  - `watch (from vue)`
### `_start(): Promise<any>`

<details><summary>Code</summary>

```ts
async function _start() {
    if (!isSupported.value || stream.value)
      return
    stream.value = await navigator!.mediaDevices.getDisplayMedia(constraint)
    stream.value?.getTracks().forEach(t => useEventListener(t, 'ended', stop, { passive: true }))
    return stream.value
  }
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `navigator!.mediaDevices.getDisplayMedia`
  - `stream.value?.getTracks().forEach`
  - `useEventListener (from ../useEventListener)`
### `_stop(): Promise<void>`

<details><summary>Code</summary>

```ts
async function _stop() {
    stream.value?.getTracks().forEach(t => t.stop())
    stream.value = undefined
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `stream.value?.getTracks().forEach`
  - `t.stop`
### `stop(): void`

<details><summary>Code</summary>

```ts
function stop() {
    _stop()
    enabled.value = false
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `_stop`
### `start(): Promise<any>`

<details><summary>Code</summary>

```ts
async function start() {
    await _start()
    if (stream.value)
      enabled.value = true
    return stream.value
  }
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `_start`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseDisplayMediaOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseDisplayMediaOptions extends ConfigurableNavigator {
  /**
   * If the stream is enabled
   * @default false
   */
  enabled?: MaybeRef<boolean>

  /**
   * If the stream video media constraints
   */
  video?: boolean | MediaTrackConstraints | undefined
  /**
   * If the stream audio media constraints
   */
  audio?: boolean | MediaTrackConstraints | undefined
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `enabled` | `MaybeRef<boolean>` | ✓ |  |
| `video` | `boolean | MediaTrackConstraints | undefined` | ✓ |  |
| `audio` | `boolean | MediaTrackConstraints | undefined` | ✓ |  |


---

## Type Aliases

### `UseDisplayMediaReturn`

```ts
type UseDisplayMediaReturn = ReturnType<typeof useDisplayMedia>;
```


---