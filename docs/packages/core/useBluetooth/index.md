[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 11 |
| ⚡ Async/Await Patterns | 3 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useBluetooth/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `tryOnMounted` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useBluetooth` | navigator?.bluetooth.requestDevice({
        acceptAllDevices,
        filters,
        optionalServices,
      }), device.value.gatt.connect() | *none* |
| async-function | `requestDevice` | navigator?.bluetooth.requestDevice({
        acceptAllDevices,
        filters,
        optionalServices,
      }) | *none* |
| async-function | `connectToBluetoothGATTServer` | device.value.gatt.connect() | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useBluetooth(options: UseBluetoothOptions): UseBluetoothReturn`

<details><summary>Code</summary>

```ts
export function useBluetooth(options?: UseBluetoothOptions): UseBluetoothReturn {
  let {
    acceptAllDevices = false,
  } = options || {}

  const {
    filters = undefined,
    optionalServices = undefined,
    navigator = defaultNavigator,
  } = options || {}

  const isSupported = useSupported(() => navigator && 'bluetooth' in navigator)

  const device = shallowRef<undefined | BluetoothDevice>()

  const error = shallowRef<unknown | null>(null)

  watch(device, () => {
    connectToBluetoothGATTServer()
  })

  async function requestDevice(): Promise<void> {
    // This is the function can only be called if Bluetooth API is supported:
    if (!isSupported.value)
      return

    // Reset any errors we currently have:
    error.value = null

    // If filters specified, we need to ensure we  don't accept all devices:
    if (filters && filters.length > 0)
      acceptAllDevices = false

    try {
      device.value = await navigator?.bluetooth.requestDevice({
        acceptAllDevices,
        filters,
        optionalServices,
      })
    }
    catch (err) {
      error.value = err
    }
  }

  const server = shallowRef<undefined | BluetoothRemoteGATTServer>()
  const isConnected = shallowRef(false)

  function reset() {
    isConnected.value = false
    device.value = undefined
    server.value = undefined
  }

  async function connectToBluetoothGATTServer() {
    // Reset any errors we currently have:
    error.value = null

    if (device.value && device.value.gatt) {
      // Add reset fn to gattserverdisconnected event:
      useEventListener(device, 'gattserverdisconnected', reset, { passive: true })

      try {
        // Connect to the device:
        server.value = await device.value.gatt.connect()
        isConnected.value = server.value.connected
      }
      catch (err) {
        error.value = err
      }
    }
  }

  tryOnMounted(() => {
    if (device.value)
      device.value.gatt?.connect()
  })

  tryOnScopeDispose(() => {
    if (device.value)
      device.value.gatt?.disconnect()
  })

  return {
    isSupported,
    isConnected: readonly(isConnected),
    // Device:
    device,
    requestDevice,
    // Server:
    server,
    // Errors:
    error,
  }
}
```
</details>

- **Parameters**:
  - `options: UseBluetoothOptions`
- **Return Type**: `UseBluetoothReturn`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `watch (from vue)`
  - `connectToBluetoothGATTServer`
  - `navigator?.bluetooth.requestDevice`
  - `useEventListener (from ../useEventListener)`
  - `device.value.gatt.connect`
  - `tryOnMounted (from @vueuse/shared)`
  - `device.value.gatt?.connect`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `device.value.gatt?.disconnect`
  - `readonly (from vue)`
- **Internal Comments**:
```
// This is the function can only be called if Bluetooth API is supported:
// Reset any errors we currently have: (x8)
// If filters specified, we need to ensure we  don't accept all devices:
// Add reset fn to gattserverdisconnected event: (x3)
// Connect to the device: (x4)
// Device: (x2)
// Server: (x2)
// Errors: (x2)
```

### `requestDevice(): Promise<void>`

<details><summary>Code</summary>

```ts
async function requestDevice(): Promise<void> {
    // This is the function can only be called if Bluetooth API is supported:
    if (!isSupported.value)
      return

    // Reset any errors we currently have:
    error.value = null

    // If filters specified, we need to ensure we  don't accept all devices:
    if (filters && filters.length > 0)
      acceptAllDevices = false

    try {
      device.value = await navigator?.bluetooth.requestDevice({
        acceptAllDevices,
        filters,
        optionalServices,
      })
    }
    catch (err) {
      error.value = err
    }
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `navigator?.bluetooth.requestDevice`
- **Internal Comments**:
```
// This is the function can only be called if Bluetooth API is supported:
// Reset any errors we currently have: (x4)
// If filters specified, we need to ensure we  don't accept all devices:
```

### `reset(): void`

<details><summary>Code</summary>

```ts
function reset() {
    isConnected.value = false
    device.value = undefined
    server.value = undefined
  }
```
</details>

- **Return Type**: `void`
### `connectToBluetoothGATTServer(): Promise<void>`

<details><summary>Code</summary>

```ts
async function connectToBluetoothGATTServer() {
    // Reset any errors we currently have:
    error.value = null

    if (device.value && device.value.gatt) {
      // Add reset fn to gattserverdisconnected event:
      useEventListener(device, 'gattserverdisconnected', reset, { passive: true })

      try {
        // Connect to the device:
        server.value = await device.value.gatt.connect()
        isConnected.value = server.value.connected
      }
      catch (err) {
        error.value = err
      }
    }
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `useEventListener (from ../useEventListener)`
  - `device.value.gatt.connect`
- **Internal Comments**:
```
// Reset any errors we currently have: (x4)
// Add reset fn to gattserverdisconnected event: (x3)
// Connect to the device: (x4)
```


---

## Interfaces

### `UseBluetoothRequestDeviceOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseBluetoothRequestDeviceOptions {
  /**
   *
   * An array of BluetoothScanFilters. This filter consists of an array
   * of BluetoothServiceUUIDs, a name parameter, and a namePrefix parameter.
   *
   */
  filters?: BluetoothLEScanFilter[] | undefined
  /**
   *
   * An array of BluetoothServiceUUIDs.
   *
   * @see https://developer.mozilla.org/en-US/docs/Web/API/BluetoothRemoteGATTService/uuid
   *
   */
  optionalServices?: BluetoothServiceUUID[] | undefined
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `filters` | `BluetoothLEScanFilter[] | undefined` | ✓ |  |
| `optionalServices` | `BluetoothServiceUUID[] | undefined` | ✓ |  |

### `UseBluetoothOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseBluetoothOptions extends UseBluetoothRequestDeviceOptions, ConfigurableNavigator {
  /**
   *
   * A boolean value indicating that the requesting script can accept all Bluetooth
   * devices. The default is false.
   *
   * !! This may result in a bunch of unrelated devices being shown
   * in the chooser and energy being wasted as there are no filters.
   *
   *
   * Use it with caution.
   *
   * @default false
   *
   */
  acceptAllDevices?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `acceptAllDevices` | `boolean` | ✓ |  |

### `UseBluetoothReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseBluetoothReturn {
  isSupported: ComputedRef<boolean>
  isConnected: Readonly<ShallowRef<boolean>>
  device: ShallowRef<BluetoothDevice | undefined>
  requestDevice: () => Promise<void>
  server: ShallowRef<BluetoothRemoteGATTServer | undefined>
  error: ShallowRef<unknown | null>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `isConnected` | `Readonly<ShallowRef<boolean>>` | ✗ |  |
| `device` | `ShallowRef<BluetoothDevice | undefined>` | ✗ |  |
| `requestDevice` | `() => Promise<void>` | ✗ |  |
| `server` | `ShallowRef<BluetoothRemoteGATTServer | undefined>` | ✗ |  |
| `error` | `ShallowRef<unknown | null>` | ✗ |  |


---