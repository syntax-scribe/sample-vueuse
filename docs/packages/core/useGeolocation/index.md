[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useGeolocation/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableNavigator` | `../_configurable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `watcher` | `number` | let/var | `*not shown*` | ✗ |


---

## Functions

### `useGeolocation(options: UseGeolocationOptions): { isSupported: any; coords: any; locatedAt: any; error: any; resume: () => void; pause: () => void; }`

<details><summary>Code</summary>

```ts
export function useGeolocation(options: UseGeolocationOptions = {}) {
  const {
    enableHighAccuracy = true,
    maximumAge = 30000,
    timeout = 27000,
    navigator = defaultNavigator,
    immediate = true,
  } = options

  const isSupported = useSupported(() => navigator && 'geolocation' in navigator)

  const locatedAt = shallowRef<number | null>(null)
  const error = shallowRef<GeolocationPositionError | null>(null)
  const coords = deepRef<Omit<GeolocationPosition['coords'], 'toJSON'>>({
    accuracy: 0,
    latitude: Number.POSITIVE_INFINITY,
    longitude: Number.POSITIVE_INFINITY,
    altitude: null,
    altitudeAccuracy: null,
    heading: null,
    speed: null,
  })

  function updatePosition(position: GeolocationPosition) {
    locatedAt.value = position.timestamp
    coords.value = position.coords
    error.value = null
  }

  let watcher: number

  function resume() {
    if (isSupported.value) {
      watcher = navigator!.geolocation.watchPosition(
        updatePosition,
        err => error.value = err,
        {
          enableHighAccuracy,
          maximumAge,
          timeout,
        },
      )
    }
  }

  if (immediate)
    resume()

  function pause() {
    if (watcher && navigator)
      navigator.geolocation.clearWatch(watcher)
  }

  tryOnScopeDispose(() => {
    pause()
  })

  return {
    isSupported,
    coords,
    locatedAt,
    error,
    resume,
    pause,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Geolocation API.
 *
 * @see https://vueuse.org/useGeolocation
 * @param options
 */
```

- **Parameters**:
  - `options: UseGeolocationOptions`
- **Return Type**: `{ isSupported: any; coords: any; locatedAt: any; error: any; resume: () => void; pause: () => void; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `deepRef (from vue)`
  - `navigator!.geolocation.watchPosition`
  - `resume`
  - `navigator.geolocation.clearWatch`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `pause`
### `updatePosition(position: GeolocationPosition): void`

<details><summary>Code</summary>

```ts
function updatePosition(position: GeolocationPosition) {
    locatedAt.value = position.timestamp
    coords.value = position.coords
    error.value = null
  }
```
</details>

- **Parameters**:
  - `position: GeolocationPosition`
- **Return Type**: `void`
### `resume(): void`

<details><summary>Code</summary>

```ts
function resume() {
    if (isSupported.value) {
      watcher = navigator!.geolocation.watchPosition(
        updatePosition,
        err => error.value = err,
        {
          enableHighAccuracy,
          maximumAge,
          timeout,
        },
      )
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `navigator!.geolocation.watchPosition`
### `pause(): void`

<details><summary>Code</summary>

```ts
function pause() {
    if (watcher && navigator)
      navigator.geolocation.clearWatch(watcher)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `navigator.geolocation.clearWatch`

---

## Interfaces

### `UseGeolocationOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseGeolocationOptions extends Partial<PositionOptions>, ConfigurableNavigator {
  immediate?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseGeolocationReturn`

```ts
type UseGeolocationReturn = ReturnType<typeof useGeolocation>;
```


---