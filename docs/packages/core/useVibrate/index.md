[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useVibrate/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `toRef` | `@vueuse/shared` |
| `useIntervalFn` | `@vueuse/shared` |
| `defaultNavigator` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `intervalControls` | `Pausable | undefined` | let/var | `*not shown*` | ✗ |


---

## Functions

### `useVibrate(options: UseVibrateOptions): { isSupported: any; pattern: any; intervalControls: any; vibrate: (pattern?: any) => void; stop: () => void; }`

<details><summary>Code</summary>

```ts
export function useVibrate(options?: UseVibrateOptions) {
  const {
    pattern = [],
    interval = 0,
    navigator = defaultNavigator,
  } = options || {}

  const isSupported = useSupported(() => typeof navigator !== 'undefined' && 'vibrate' in navigator)

  const patternRef = toRef(pattern)
  let intervalControls: Pausable | undefined

  const vibrate = (pattern = patternRef.value) => {
    if (isSupported.value)
      navigator!.vibrate(pattern)
  }

  // Attempt to stop the vibration:
  const stop = () => {
    // Stope the vibration if we need to:
    if (isSupported.value)
      navigator!.vibrate(0)
    intervalControls?.pause()
  }

  if (interval > 0) {
    intervalControls = useIntervalFn(
      vibrate,
      interval,
      {
        immediate: false,
        immediateCallback: false,
      },
    )
  }

  return {
    isSupported,
    pattern,
    intervalControls,
    vibrate,
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive vibrate
 *
 * @see https://vueuse.org/useVibrate
 * @see https://developer.mozilla.org/en-US/docs/Web/API/Vibration_API
 * @param options
 */
```

- **Parameters**:
  - `options: UseVibrateOptions`
- **Return Type**: `{ isSupported: any; pattern: any; intervalControls: any; vibrate: (pattern?: any) => void; stop: () => void; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `toRef (from @vueuse/shared)`
  - `navigator!.vibrate`
  - `intervalControls?.pause`
  - `useIntervalFn (from @vueuse/shared)`
- **Internal Comments**:
```
// Attempt to stop the vibration: (x2)
// Stope the vibration if we need to:
```

### `vibrate(pattern: any): void`

<details><summary>Code</summary>

```ts
(pattern = patternRef.value) => {
    if (isSupported.value)
      navigator!.vibrate(pattern)
  }
```
</details>

- **Parameters**:
  - `pattern: any`
- **Return Type**: `void`
- **Calls**:
  - `navigator!.vibrate`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    // Stope the vibration if we need to:
    if (isSupported.value)
      navigator!.vibrate(0)
    intervalControls?.pause()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `navigator!.vibrate`
  - `intervalControls?.pause`
- **Internal Comments**:
```
// Stope the vibration if we need to:
```


---

## Interfaces

### `UseVibrateOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseVibrateOptions extends ConfigurableNavigator {
  /**
   *
   * Vibration Pattern
   *
   * An array of values describes alternating periods in which the
   * device is vibrating and not vibrating. Each value in the array
   * is converted to an integer, then interpreted alternately as
   * the number of milliseconds the device should vibrate and the
   * number of milliseconds it should not be vibrating
   *
   * @default []
   *
   */
  pattern?: MaybeRefOrGetter<number[] | number>
  /**
   * Interval to run a persistent vibration, in ms
   *
   * Pass `0` to disable
   *
   * @default 0
   *
   */
  interval?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `pattern` | `MaybeRefOrGetter<number[] | number>` | ✓ |  |
| `interval` | `number` | ✓ |  |


---

## Type Aliases

### `UseVibrateReturn`

```ts
type UseVibrateReturn = ReturnType<typeof useVibrate>;
```


---