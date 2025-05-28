[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 4 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `video` | `boolean | MediaTrackConstraints` | const | `options.video` | ✗ |
| `audio` | `boolean | MediaTrackConstraints` | const | `options.audio` | ✗ |
| `constraint` | `MediaStreamConstraints` | const | `{ audio, video }` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useDisplayMedia` | navigator!.mediaDevices.getDisplayMedia(constraint), _start() | *none* |
| async-function | `_start` | navigator!.mediaDevices.getDisplayMedia(constraint) | *none* |
| async-function | `_stop` | *none* | *none* |
| async-function | `start` | _start() | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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