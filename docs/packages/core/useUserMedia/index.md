[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 7 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 4 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useUserMedia/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useUserMedia` | navigator!.mediaDevices.getUserMedia({
      video: getDeviceOptions('video'),
      audio: getDeviceOptions('audio'),
    }), _start(), start() | *none* |
| async-function | `_start` | navigator!.mediaDevices.getUserMedia({
      video: getDeviceOptions('video'),
      audio: getDeviceOptions('audio'),
    }) | *none* |
| async-function | `start` | _start() | *none* |
| async-function | `restart` | start() | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `useUserMedia(options: UseUserMediaOptions): { isSupported: any; stream: Ref<MediaStream>; start: () => Promise<any>; stop: () => void; restart: () => Promise<any>; constraints: any; enabled: any; autoSwitch: any; }`

<details><summary>Code</summary>

```ts
export function useUserMedia(options: UseUserMediaOptions = {}) {
  const enabled = shallowRef(options.enabled ?? false)
  const autoSwitch = shallowRef(options.autoSwitch ?? true)
  const constraints = deepRef(options.constraints)
  const { navigator = defaultNavigator } = options
  const isSupported = useSupported(() => navigator?.mediaDevices?.getUserMedia)

  const stream: Ref<MediaStream | undefined> = shallowRef()

  function getDeviceOptions(type: 'video' | 'audio') {
    switch (type) {
      case 'video': {
        if (constraints.value)
          return constraints.value.video || false
        break
      }
      case 'audio': {
        if (constraints.value)
          return constraints.value.audio || false
        break
      }
    }
  }

  async function _start() {
    if (!isSupported.value || stream.value)
      return
    stream.value = await navigator!.mediaDevices.getUserMedia({
      video: getDeviceOptions('video'),
      audio: getDeviceOptions('audio'),
    })
    return stream.value
  }

  function _stop() {
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

  async function restart() {
    _stop()
    return await start()
  }

  watch(
    enabled,
    (v) => {
      if (v)
        _start()
      else _stop()
    },
    { immediate: true },
  )

  watch(
    constraints,
    () => {
      if (autoSwitch.value && stream.value)
        restart()
    },
    { immediate: true },
  )

  tryOnScopeDispose(() => {
    stop()
  })

  return {
    isSupported,
    stream,
    start,
    stop,
    restart,
    constraints,
    enabled,
    autoSwitch,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `mediaDevices.getUserMedia` streaming
 *
 * @see https://vueuse.org/useUserMedia
 * @param options
 */
```

- **Parameters**:
  - `options: UseUserMediaOptions`
- **Return Type**: `{ isSupported: any; stream: Ref<MediaStream>; start: () => Promise<any>; stop: () => void; restart: () => Promise<any>; constraints: any; enabled: any; autoSwitch: any; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `useSupported (from ../useSupported)`
  - `navigator!.mediaDevices.getUserMedia`
  - `getDeviceOptions`
  - `stream.value?.getTracks().forEach`
  - `t.stop`
  - `_stop`
  - `_start`
  - `start`
  - `watch (from vue)`
  - `restart`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `stop`
### `getDeviceOptions(type: 'video' | 'audio'): any`

<details><summary>Code</summary>

```ts
function getDeviceOptions(type: 'video' | 'audio') {
    switch (type) {
      case 'video': {
        if (constraints.value)
          return constraints.value.video || false
        break
      }
      case 'audio': {
        if (constraints.value)
          return constraints.value.audio || false
        break
      }
    }
  }
```
</details>

- **Parameters**:
  - `type: 'video' | 'audio'`
- **Return Type**: `any`
### `_start(): Promise<any>`

<details><summary>Code</summary>

```ts
async function _start() {
    if (!isSupported.value || stream.value)
      return
    stream.value = await navigator!.mediaDevices.getUserMedia({
      video: getDeviceOptions('video'),
      audio: getDeviceOptions('audio'),
    })
    return stream.value
  }
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `navigator!.mediaDevices.getUserMedia`
  - `getDeviceOptions`
### `_stop(): void`

<details><summary>Code</summary>

```ts
function _stop() {
    stream.value?.getTracks().forEach(t => t.stop())
    stream.value = undefined
  }
```
</details>

- **Return Type**: `void`
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
### `restart(): Promise<any>`

<details><summary>Code</summary>

```ts
async function restart() {
    _stop()
    return await start()
  }
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `_stop`
  - `start`

---

## Interfaces

### `UseUserMediaOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseUserMediaOptions extends ConfigurableNavigator {
  /**
   * If the stream is enabled
   * @default false
   */
  enabled?: MaybeRef<boolean>
  /**
   * Recreate stream when deviceIds or constraints changed
   *
   * @default true
   */
  autoSwitch?: MaybeRef<boolean>
  /**
   * MediaStreamConstraints to be applied to the requested MediaStream
   * If provided, the constraints will override videoDeviceId and audioDeviceId
   *
   * @default {}
   */
  constraints?: MaybeRef<MediaStreamConstraints>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `enabled` | `MaybeRef<boolean>` | ✓ |  |
| `autoSwitch` | `MaybeRef<boolean>` | ✓ |  |
| `constraints` | `MaybeRef<MediaStreamConstraints>` | ✓ |  |


---

## Type Aliases

### `UseUserMediaReturn`

```ts
type UseUserMediaReturn = ReturnType<typeof useUserMedia>;
```


---