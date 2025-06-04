[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 4 |
| ⚡ Async/Await Patterns | 3 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useDevicesList/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `usePermission` | `../usePermission` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `devices` | `Ref<MediaDeviceInfo[]>` | const | `deepRef([]) as Ref<MediaDeviceInfo[]>` | ✗ |
| `stream` | `MediaStream | null` | let/var | `*not shown*` | ✗ |
| `deviceName` | `"camera" | "microphone"` | let/var | `constraints.video ? 'camera' : 'microphone'` | ✗ |
| `granted` | `boolean` | let/var | `true` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useDevicesList` | navigator!.mediaDevices.enumerateDevices(), query(), navigator!.mediaDevices.getUserMedia(constraints) | *none* |
| async-function | `update` | navigator!.mediaDevices.enumerateDevices() | *none* |
| async-function | `ensurePermissions` | query(), navigator!.mediaDevices.getUserMedia(constraints) | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useDevicesList(options: UseDevicesListOptions): UseDevicesListReturn`

<details><summary>Code</summary>

```ts
export function useDevicesList(options: UseDevicesListOptions = {}): UseDevicesListReturn {
  const {
    navigator = defaultNavigator,
    requestPermissions = false,
    constraints = { audio: true, video: true },
    onUpdated,
  } = options

  const devices = deepRef([]) as Ref<MediaDeviceInfo[]>
  const videoInputs = computed(() => devices.value.filter(i => i.kind === 'videoinput'))
  const audioInputs = computed(() => devices.value.filter(i => i.kind === 'audioinput'))
  const audioOutputs = computed(() => devices.value.filter(i => i.kind === 'audiooutput'))
  const isSupported = useSupported(() => navigator && navigator.mediaDevices && navigator.mediaDevices.enumerateDevices)
  const permissionGranted = shallowRef(false)
  let stream: MediaStream | null

  async function update() {
    if (!isSupported.value)
      return

    devices.value = await navigator!.mediaDevices.enumerateDevices()
    onUpdated?.(devices.value)
    if (stream) {
      stream.getTracks().forEach(t => t.stop())
      stream = null
    }
  }

  async function ensurePermissions() {
    const deviceName = constraints.video ? 'camera' : 'microphone'

    if (!isSupported.value)
      return false

    if (permissionGranted.value)
      return true

    const { state, query } = usePermission(deviceName, { controls: true })
    await query()
    if (state.value !== 'granted') {
      let granted = true
      try {
        stream = await navigator!.mediaDevices.getUserMedia(constraints)
      }
      catch {
        stream = null
        granted = false
      }
      update()
      permissionGranted.value = granted
    }
    else {
      permissionGranted.value = true
    }

    return permissionGranted.value
  }

  if (isSupported.value) {
    if (requestPermissions)
      ensurePermissions()

    useEventListener(navigator!.mediaDevices, 'devicechange', update, { passive: true })
    update()
  }

  return {
    devices,
    ensurePermissions,
    permissionGranted,
    videoInputs,
    audioInputs,
    audioOutputs,
    isSupported,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `enumerateDevices` listing available input/output devices
 *
 * @see https://vueuse.org/useDevicesList
 * @param options
 */
```

- **Parameters**:
  - `options: UseDevicesListOptions`
- **Return Type**: `UseDevicesListReturn`
- **Calls**:
  - `deepRef (from vue)`
  - `computed (from vue)`
  - `devices.value.filter`
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `navigator!.mediaDevices.enumerateDevices`
  - `onUpdated`
  - `stream.getTracks().forEach`
  - `t.stop`
  - `usePermission (from ../usePermission)`
  - `query`
  - `navigator!.mediaDevices.getUserMedia`
  - `update`
  - `ensurePermissions`
  - `useEventListener (from ../useEventListener)`
### `update(): Promise<void>`

<details><summary>Code</summary>

```ts
async function update() {
    if (!isSupported.value)
      return

    devices.value = await navigator!.mediaDevices.enumerateDevices()
    onUpdated?.(devices.value)
    if (stream) {
      stream.getTracks().forEach(t => t.stop())
      stream = null
    }
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `navigator!.mediaDevices.enumerateDevices`
  - `onUpdated`
  - `stream.getTracks().forEach`
  - `t.stop`
### `ensurePermissions(): Promise<any>`

<details><summary>Code</summary>

```ts
async function ensurePermissions() {
    const deviceName = constraints.video ? 'camera' : 'microphone'

    if (!isSupported.value)
      return false

    if (permissionGranted.value)
      return true

    const { state, query } = usePermission(deviceName, { controls: true })
    await query()
    if (state.value !== 'granted') {
      let granted = true
      try {
        stream = await navigator!.mediaDevices.getUserMedia(constraints)
      }
      catch {
        stream = null
        granted = false
      }
      update()
      permissionGranted.value = granted
    }
    else {
      permissionGranted.value = true
    }

    return permissionGranted.value
  }
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `usePermission (from ../usePermission)`
  - `query`
  - `navigator!.mediaDevices.getUserMedia`
  - `update`

---

## Interfaces

### `UseDevicesListOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseDevicesListOptions extends ConfigurableNavigator {
  onUpdated?: (devices: MediaDeviceInfo[]) => void
  /**
   * Request for permissions immediately if it's not granted,
   * otherwise label and deviceIds could be empty
   *
   * @default false
   */
  requestPermissions?: boolean
  /**
   * Request for types of media permissions
   *
   * @default { audio: true, video: true }
   */
  constraints?: MediaStreamConstraints
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `onUpdated` | `(devices: MediaDeviceInfo[]) => void` | ✓ |  |
| `requestPermissions` | `boolean` | ✓ |  |
| `constraints` | `MediaStreamConstraints` | ✓ |  |

### `UseDevicesListReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseDevicesListReturn {
  /**
   * All devices
   */
  devices: Ref<MediaDeviceInfo[]>
  videoInputs: ComputedRef<MediaDeviceInfo[]>
  audioInputs: ComputedRef<MediaDeviceInfo[]>
  audioOutputs: ComputedRef<MediaDeviceInfo[]>
  permissionGranted: ShallowRef<boolean>
  ensurePermissions: () => Promise<boolean>
  isSupported: ComputedRef<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `devices` | `Ref<MediaDeviceInfo[]>` | ✗ |  |
| `videoInputs` | `ComputedRef<MediaDeviceInfo[]>` | ✗ |  |
| `audioInputs` | `ComputedRef<MediaDeviceInfo[]>` | ✗ |  |
| `audioOutputs` | `ComputedRef<MediaDeviceInfo[]>` | ✗ |  |
| `permissionGranted` | `ShallowRef<boolean>` | ✗ |  |
| `ensurePermissions` | `() => Promise<boolean>` | ✗ |  |
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |


---