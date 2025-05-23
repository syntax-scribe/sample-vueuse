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
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 3

## 🛠️ File Location:
📂 **`packages/core/useScreenOrientation/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useScreenOrientation(options: ConfigurableWindow): { isSupported: any; orientation: any; angle: any; lockOrientation: (type: OrientationLockType) => Promise<void>; unlockOrientation: () => void; }`

<details><summary>Code</summary>

```ts
export function useScreenOrientation(options: ConfigurableWindow = {}) {
  const {
    window = defaultWindow,
  } = options

  const isSupported = useSupported(() => window && 'screen' in window && 'orientation' in window.screen)

  const screenOrientation = (isSupported.value ? window!.screen.orientation : {}) as ScreenOrientation

  const orientation = deepRef<OrientationType | undefined>(screenOrientation.type)
  const angle = shallowRef(screenOrientation.angle || 0)

  if (isSupported.value) {
    useEventListener(window, 'orientationchange', () => {
      orientation.value = screenOrientation.type
      angle.value = screenOrientation.angle
    }, { passive: true })
  }

  const lockOrientation = (type: OrientationLockType) => {
    if (isSupported.value && typeof screenOrientation.lock === 'function')
      return screenOrientation.lock(type)

    return Promise.reject(new Error('Not supported'))
  }

  const unlockOrientation = () => {
    if (isSupported.value && typeof screenOrientation.unlock === 'function')
      screenOrientation.unlock()
  }

  return {
    isSupported,
    orientation,
    angle,
    lockOrientation,
    unlockOrientation,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive screen orientation
 *
 * @see https://vueuse.org/useScreenOrientation
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `{ isSupported: any; orientation: any; angle: any; lockOrientation: (type: OrientationLockType) => Promise<void>; unlockOrientation: () => void; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `deepRef (from vue)`
  - `shallowRef (from vue)`
  - `useEventListener (from ../useEventListener)`
  - `screenOrientation.lock`
  - `Promise.reject`
  - `screenOrientation.unlock`
### `lockOrientation(type: OrientationLockType): Promise<void>`

<details><summary>Code</summary>

```ts
(type: OrientationLockType) => {
    if (isSupported.value && typeof screenOrientation.lock === 'function')
      return screenOrientation.lock(type)

    return Promise.reject(new Error('Not supported'))
  }
```
</details>

- **Parameters**:
  - `type: OrientationLockType`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `screenOrientation.lock`
  - `Promise.reject`
### `unlockOrientation(): void`

<details><summary>Code</summary>

```ts
() => {
    if (isSupported.value && typeof screenOrientation.unlock === 'function')
      screenOrientation.unlock()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `screenOrientation.unlock`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `ScreenOrientation`

<details><summary>Interface Code</summary>

```ts
export interface ScreenOrientation extends EventTarget {
  lock: (orientation: OrientationLockType) => Promise<void>
  unlock: () => void
  readonly type: OrientationType
  readonly angle: number
  addEventListener: (type: 'change', listener: (this: this, ev: Event) => any, useCapture?: boolean) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `lock` | `(orientation: OrientationLockType) => Promise<void>` | ✗ |  |
| `unlock` | `() => void` | ✗ |  |
| `type` | `OrientationType` | ✗ |  |
| `angle` | `number` | ✗ |  |
| `addEventListener` | `(type: 'change', listener: (this: this, ev: Event) => any, useCapture?: boolean) => void` | ✗ |  |


---

## Type Aliases

### `OrientationType`

```ts
type OrientationType = 'portrait-primary' | 'portrait-secondary' | 'landscape-primary' | 'landscape-secondary';
```

### `OrientationLockType`

```ts
type OrientationLockType = 'any' | 'natural' | 'landscape' | 'portrait' | 'portrait-primary' | 'portrait-secondary' | 'landscape-primary' | 'landscape-secondary';
```

### `UseScreenOrientationReturn`

```ts
type UseScreenOrientationReturn = ReturnType<typeof useScreenOrientation>;
```


---