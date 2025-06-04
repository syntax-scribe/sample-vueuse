[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
| ⚡ Async/Await Patterns | 2 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `screenOrientation` | `ScreenOrientation` | const | `(isSupported.value ? window!.screen.orientation : {}) as ScreenOrientation` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `useScreenOrientation` | *none* | Promise.reject |
| promise-chain | `lockOrientation` | *none* | Promise.reject |


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