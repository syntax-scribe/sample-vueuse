[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 1
- **Type Aliases**: 3

## 🛠️ File Location:
📂 **`packages/core/useNetwork/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useNetwork(options: ConfigurableWindow): Readonly<NetworkState>`

<details><summary>Code</summary>

```ts
export function useNetwork(options: ConfigurableWindow = {}): Readonly<NetworkState> {
  const { window = defaultWindow } = options
  const navigator = window?.navigator
  const isSupported = useSupported(() => navigator && 'connection' in navigator)

  const isOnline = shallowRef(true)
  const saveData = shallowRef(false)
  const offlineAt = shallowRef<number | undefined>(undefined)
  const onlineAt = shallowRef<number | undefined>(undefined)
  const downlink = shallowRef<number | undefined>(undefined)
  const downlinkMax = shallowRef<number | undefined>(undefined)
  const rtt = shallowRef<number | undefined>(undefined)
  const effectiveType = shallowRef<NetworkEffectiveType>(undefined)
  const type = shallowRef<NetworkType>('unknown')

  const connection = isSupported.value && (navigator as any).connection

  function updateNetworkInformation() {
    if (!navigator)
      return

    isOnline.value = navigator.onLine
    offlineAt.value = isOnline.value ? undefined : Date.now()
    onlineAt.value = isOnline.value ? Date.now() : undefined

    if (connection) {
      downlink.value = connection.downlink
      downlinkMax.value = connection.downlinkMax
      effectiveType.value = connection.effectiveType
      rtt.value = connection.rtt
      saveData.value = connection.saveData
      type.value = connection.type
    }
  }

  const listenerOptions = { passive: true }

  if (window) {
    useEventListener(window, 'offline', () => {
      isOnline.value = false
      offlineAt.value = Date.now()
    }, listenerOptions)

    useEventListener(window, 'online', () => {
      isOnline.value = true
      onlineAt.value = Date.now()
    }, listenerOptions)
  }

  if (connection)
    useEventListener(connection, 'change', updateNetworkInformation, listenerOptions)

  updateNetworkInformation()

  return {
    isSupported,
    isOnline: readonly(isOnline),
    saveData: readonly(saveData),
    offlineAt: readonly(offlineAt),
    onlineAt: readonly(onlineAt),
    downlink: readonly(downlink),
    downlinkMax: readonly(downlinkMax),
    effectiveType: readonly(effectiveType),
    rtt: readonly(rtt),
    type: readonly(type),
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Network status.
 *
 * @see https://vueuse.org/useNetwork
 * @param options
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `Readonly<NetworkState>`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `Date.now`
  - `useEventListener (from ../useEventListener)`
  - `updateNetworkInformation`
  - `readonly (from vue)`
### `updateNetworkInformation(): void`

<details><summary>Code</summary>

```ts
function updateNetworkInformation() {
    if (!navigator)
      return

    isOnline.value = navigator.onLine
    offlineAt.value = isOnline.value ? undefined : Date.now()
    onlineAt.value = isOnline.value ? Date.now() : undefined

    if (connection) {
      downlink.value = connection.downlink
      downlinkMax.value = connection.downlinkMax
      effectiveType.value = connection.effectiveType
      rtt.value = connection.rtt
      saveData.value = connection.saveData
      type.value = connection.type
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `Date.now`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `NetworkState`

<details><summary>Interface Code</summary>

```ts
export interface NetworkState {
  isSupported: ComputedRef<boolean>
  /**
   * If the user is currently connected.
   */
  isOnline: Readonly<ShallowRef<boolean>>
  /**
   * The time since the user was last connected.
   */
  offlineAt: Readonly<ShallowRef<number | undefined>>
  /**
   * At this time, if the user is offline and reconnects
   */
  onlineAt: Readonly<ShallowRef<number | undefined>>
  /**
   * The download speed in Mbps.
   */
  downlink: Readonly<ShallowRef<number | undefined>>
  /**
   * The max reachable download speed in Mbps.
   */
  downlinkMax: Readonly<ShallowRef<number | undefined>>
  /**
   * The detected effective speed type.
   */
  effectiveType: Readonly<ShallowRef<NetworkEffectiveType | undefined>>
  /**
   * The estimated effective round-trip time of the current connection.
   */
  rtt: Readonly<ShallowRef<number | undefined>>
  /**
   * If the user activated data saver mode.
   */
  saveData: Readonly<ShallowRef<boolean | undefined>>
  /**
   * The detected connection/network type.
   */
  type: Readonly<ShallowRef<NetworkType>>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `isOnline` | `Readonly<ShallowRef<boolean>>` | ✗ |  |
| `offlineAt` | `Readonly<ShallowRef<number | undefined>>` | ✗ |  |
| `onlineAt` | `Readonly<ShallowRef<number | undefined>>` | ✗ |  |
| `downlink` | `Readonly<ShallowRef<number | undefined>>` | ✗ |  |
| `downlinkMax` | `Readonly<ShallowRef<number | undefined>>` | ✗ |  |
| `effectiveType` | `Readonly<ShallowRef<NetworkEffectiveType | undefined>>` | ✗ |  |
| `rtt` | `Readonly<ShallowRef<number | undefined>>` | ✗ |  |
| `saveData` | `Readonly<ShallowRef<boolean | undefined>>` | ✗ |  |
| `type` | `Readonly<ShallowRef<NetworkType>>` | ✗ |  |


---

## Type Aliases

### `NetworkType`

```ts
type NetworkType = 'bluetooth' | 'cellular' | 'ethernet' | 'none' | 'wifi' | 'wimax' | 'other' | 'unknown';
```

### `NetworkEffectiveType`

```ts
type NetworkEffectiveType = 'slow-2g' | '2g' | '3g' | '4g' | undefined;
```

### `UseNetworkReturn`

```ts
type UseNetworkReturn = ReturnType<typeof useNetwork>;
```


---