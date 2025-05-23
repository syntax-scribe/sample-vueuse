[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 5
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useCountdown/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `useIntervalFn` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `useCountdown(initialCountdown: MaybeRefOrGetter<number>, options: UseCountdownOptions): UseCountdownReturn`

<details><summary>Code</summary>

```ts
export function useCountdown(initialCountdown: MaybeRefOrGetter<number>, options?: UseCountdownOptions): UseCountdownReturn {
  const remaining = shallowRef(toValue(initialCountdown))

  const intervalController = useIntervalFn(() => {
    const value = remaining.value - 1
    remaining.value = value < 0 ? 0 : value
    options?.onTick?.()
    if (remaining.value <= 0) {
      intervalController.pause()
      options?.onComplete?.()
    }
  }, options?.interval ?? 1000, { immediate: options?.immediate ?? false })

  const reset = (countdown?: MaybeRefOrGetter<number>) => {
    remaining.value = toValue(countdown) ?? toValue(initialCountdown)
  }

  const stop = () => {
    intervalController.pause()
    reset()
  }

  const resume = () => {
    if (!intervalController.isActive.value) {
      if (remaining.value > 0) {
        intervalController.resume()
      }
    }
  }

  const start = (countdown?: MaybeRefOrGetter<number>) => {
    reset(countdown)
    intervalController.resume()
  }

  return {
    remaining,
    reset,
    stop,
    start,
    pause: intervalController.pause,
    resume,
    isActive: intervalController.isActive,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Wrapper for `useIntervalFn` that provides a countdown timer in seconds.
 *
 * @param initialCountdown
 * @param options
 *
 * @see https://vueuse.org/useCountdown
 */
```

- **Parameters**:
  - `initialCountdown: MaybeRefOrGetter<number>`
  - `options: UseCountdownOptions`
- **Return Type**: `UseCountdownReturn`
- **Calls**:
  - `shallowRef (from vue)`
  - `toValue (from vue)`
  - `useIntervalFn (from @vueuse/shared)`
  - `options?.onTick`
  - `intervalController.pause`
  - `options?.onComplete`
  - `reset`
  - `intervalController.resume`
### `reset(countdown: MaybeRefOrGetter<number>): void`

<details><summary>Code</summary>

```ts
(countdown?: MaybeRefOrGetter<number>) => {
    remaining.value = toValue(countdown) ?? toValue(initialCountdown)
  }
```
</details>

- **Parameters**:
  - `countdown: MaybeRefOrGetter<number>`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    intervalController.pause()
    reset()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `intervalController.pause`
  - `reset`
### `resume(): void`

<details><summary>Code</summary>

```ts
() => {
    if (!intervalController.isActive.value) {
      if (remaining.value > 0) {
        intervalController.resume()
      }
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `intervalController.resume`
### `start(countdown: MaybeRefOrGetter<number>): void`

<details><summary>Code</summary>

```ts
(countdown?: MaybeRefOrGetter<number>) => {
    reset(countdown)
    intervalController.resume()
  }
```
</details>

- **Parameters**:
  - `countdown: MaybeRefOrGetter<number>`
- **Return Type**: `void`
- **Calls**:
  - `reset`
  - `intervalController.resume`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseCountdownOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseCountdownOptions {
  /**
   *  Interval for the countdown in milliseconds. Default is 1000ms.
   */
  interval?: MaybeRefOrGetter<number>
  /**
   * Callback function called when the countdown reaches 0.
   */
  onComplete?: () => void
  /**
   * Callback function called on each tick of the countdown.
   */
  onTick?: () => void
  /**
   * Start the countdown immediately
   *
   * @default false
   */
  immediate?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `interval` | `MaybeRefOrGetter<number>` | ✓ |  |
| `onComplete` | `() => void` | ✓ |  |
| `onTick` | `() => void` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |

### `UseCountdownReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseCountdownReturn extends Pausable {
  /**
   * Current countdown value.
   */
  remaining: ShallowRef<number>
  /**
   * Resets the countdown and repeatsLeft to their initial values.
   */
  reset: (countdown?: MaybeRefOrGetter<number>) => void
  /**
   * Stops the countdown and resets its state.
   */
  stop: () => void
  /**
   * Reset the countdown and start it again.
   */
  start: (countdown?: MaybeRefOrGetter<number>) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `remaining` | `ShallowRef<number>` | ✗ |  |
| `reset` | `(countdown?: MaybeRefOrGetter<number>) => void` | ✗ |  |
| `stop` | `() => void` | ✗ |  |
| `start` | `(countdown?: MaybeRefOrGetter<number>) => void` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---