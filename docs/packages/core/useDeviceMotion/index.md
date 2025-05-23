[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useDeviceMotion/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableEventFilter` | `@vueuse/shared` |
| `Ref` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `bypassFilter` | `@vueuse/shared` |
| `createFilterWrapper` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useDeviceMotion(options: DeviceMotionOptions): { acceleration: Ref<DeviceMotionEventAcceleration>; accelerationIncludingGravity: Ref<DeviceMotionEventAcceleration>; ... 5 more ...; permissionGranted: any; }`

<details><summary>Code</summary>

```ts
export function useDeviceMotion(options: DeviceMotionOptions = {}) {
  const {
    window = defaultWindow,
    requestPermissions = false,
    eventFilter = bypassFilter,
  } = options

  const isSupported = useSupported(() => typeof DeviceMotionEvent !== 'undefined')
  const requirePermissions = useSupported(() => isSupported.value && 'requestPermission' in DeviceMotionEvent && typeof DeviceMotionEvent.requestPermission === 'function')
  const permissionGranted = shallowRef(false)
  const acceleration: Ref<DeviceMotionEvent['acceleration']> = deepRef({ x: null, y: null, z: null })
  const rotationRate: Ref<DeviceMotionEvent['rotationRate']> = deepRef({ alpha: null, beta: null, gamma: null })
  const interval = shallowRef(0)
  const accelerationIncludingGravity: Ref<DeviceMotionEvent['accelerationIncludingGravity']> = deepRef({
    x: null,
    y: null,
    z: null,
  })

  function init() {
    if (window) {
      const onDeviceMotion = createFilterWrapper(
        eventFilter,
        (event: DeviceMotionEvent) => {
          acceleration.value = {
            x: event.acceleration?.x || null,
            y: event.acceleration?.y || null,
            z: event.acceleration?.z || null,
          }
          accelerationIncludingGravity.value = {
            x: event.accelerationIncludingGravity?.x || null,
            y: event.accelerationIncludingGravity?.y || null,
            z: event.accelerationIncludingGravity?.z || null,
          }
          rotationRate.value = {
            alpha: event.rotationRate?.alpha || null,
            beta: event.rotationRate?.beta || null,
            gamma: event.rotationRate?.gamma || null,
          }
          interval.value = event.interval
        },
      )

      useEventListener(window, 'devicemotion', onDeviceMotion, { passive: true })
    }
  }

  const ensurePermissions = async () => {
    if (!requirePermissions.value)
      permissionGranted.value = true

    if (permissionGranted.value)
      return
    if (requirePermissions.value) {
      const requestPermission = (DeviceMotionEvent as unknown as DeviceMotionEventiOS).requestPermission
      try {
        const response = await requestPermission()
        if (response === 'granted') {
          permissionGranted.value = true
          init()
        }
      }
      catch (error) {
        console.error(error)
      }
    }
  }

  if (isSupported.value) {
    if (requestPermissions && requirePermissions.value) {
      ensurePermissions()
        .then(() => init())
    }
    else {
      init()
    }
  }

  return {
    acceleration,
    accelerationIncludingGravity,
    rotationRate,
    interval,
    isSupported,
    requirePermissions,
    ensurePermissions,
    permissionGranted,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive DeviceMotionEvent.
 *
 * @see https://vueuse.org/useDeviceMotion
 * @param options
 */
```

- **Parameters**:
  - `options: DeviceMotionOptions`
- **Return Type**: `{ acceleration: Ref<DeviceMotionEventAcceleration>; accelerationIncludingGravity: Ref<DeviceMotionEventAcceleration>; ... 5 more ...; permissionGranted: any; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `createFilterWrapper (from @vueuse/shared)`
  - `useEventListener (from ../useEventListener)`
  - `requestPermission`
  - `init`
  - `console.error`
  - `ensurePermissions()
        .then`
### `init(): void`

<details><summary>Code</summary>

```ts
function init() {
    if (window) {
      const onDeviceMotion = createFilterWrapper(
        eventFilter,
        (event: DeviceMotionEvent) => {
          acceleration.value = {
            x: event.acceleration?.x || null,
            y: event.acceleration?.y || null,
            z: event.acceleration?.z || null,
          }
          accelerationIncludingGravity.value = {
            x: event.accelerationIncludingGravity?.x || null,
            y: event.accelerationIncludingGravity?.y || null,
            z: event.accelerationIncludingGravity?.z || null,
          }
          rotationRate.value = {
            alpha: event.rotationRate?.alpha || null,
            beta: event.rotationRate?.beta || null,
            gamma: event.rotationRate?.gamma || null,
          }
          interval.value = event.interval
        },
      )

      useEventListener(window, 'devicemotion', onDeviceMotion, { passive: true })
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `createFilterWrapper (from @vueuse/shared)`
  - `useEventListener (from ../useEventListener)`
### `ensurePermissions(): Promise<void>`

<details><summary>Code</summary>

```ts
async () => {
    if (!requirePermissions.value)
      permissionGranted.value = true

    if (permissionGranted.value)
      return
    if (requirePermissions.value) {
      const requestPermission = (DeviceMotionEvent as unknown as DeviceMotionEventiOS).requestPermission
      try {
        const response = await requestPermission()
        if (response === 'granted') {
          permissionGranted.value = true
          init()
        }
      }
      catch (error) {
        console.error(error)
      }
    }
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `requestPermission`
  - `init`
  - `console.error`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `DeviceMotionOptions`

<details><summary>Interface Code</summary>

```ts
export interface DeviceMotionOptions extends ConfigurableWindow, ConfigurableEventFilter {
  /**
   * Request for permissions immediately if it's not granted,
   * otherwise label and deviceIds could be empty
   *
   * @default false
   */
  requestPermissions?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `requestPermissions` | `boolean` | ✓ |  |

### `DeviceMotionEventiOS`

<details><summary>Interface Code</summary>

```ts
interface DeviceMotionEventiOS extends DeviceMotionOptions {
  requestPermission: () => Promise<'granted' | 'denied'>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `requestPermission` | `() => Promise<'granted' | 'denied'>` | ✗ |  |


---

## Type Aliases

### `UseDeviceMotionReturn`

```ts
type UseDeviceMotionReturn = ReturnType<typeof useDeviceMotion>;
```


---