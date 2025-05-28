[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useRafFn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `previousFrameTimestamp` | `number` | let/var | `0` | ✗ |
| `rafId` | `null | number` | let/var | `null` | ✗ |
| `delta` | `number` | const | `timestamp - previousFrameTimestamp` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useRafFn(fn: (args: UseRafFnCallbackArguments) => void, options: UseRafFnOptions): Pausable`

<details><summary>Code</summary>

```ts
export function useRafFn(fn: (args: UseRafFnCallbackArguments) => void, options: UseRafFnOptions = {}): Pausable {
  const {
    immediate = true,
    fpsLimit = undefined,
    window = defaultWindow,
    once = false,
  } = options

  const isActive = shallowRef(false)
  const intervalLimit = computed(() => {
    return fpsLimit ? 1000 / toValue(fpsLimit) : null
  })
  let previousFrameTimestamp = 0
  let rafId: null | number = null

  function loop(timestamp: DOMHighResTimeStamp) {
    if (!isActive.value || !window)
      return

    if (!previousFrameTimestamp)
      previousFrameTimestamp = timestamp

    const delta = timestamp - previousFrameTimestamp

    if (intervalLimit.value && delta < intervalLimit.value) {
      rafId = window.requestAnimationFrame(loop)
      return
    }

    previousFrameTimestamp = timestamp
    fn({ delta, timestamp })
    if (once) {
      isActive.value = false
      rafId = null
      return
    }
    rafId = window.requestAnimationFrame(loop)
  }

  function resume() {
    if (!isActive.value && window) {
      isActive.value = true
      previousFrameTimestamp = 0
      rafId = window.requestAnimationFrame(loop)
    }
  }

  function pause() {
    isActive.value = false
    if (rafId != null && window) {
      window.cancelAnimationFrame(rafId)
      rafId = null
    }
  }

  if (immediate)
    resume()

  tryOnScopeDispose(pause)

  return {
    isActive: readonly(isActive),
    pause,
    resume,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Call function on every `requestAnimationFrame`. With controls of pausing and resuming.
 *
 * @see https://vueuse.org/useRafFn
 * @param fn
 * @param options
 */
```

- **Parameters**:
  - `fn: (args: UseRafFnCallbackArguments) => void`
  - `options: UseRafFnOptions`
- **Return Type**: `Pausable`
- **Calls**:
  - `shallowRef (from vue)`
  - `computed (from vue)`
  - `toValue (from vue)`
  - `window.requestAnimationFrame`
  - `fn`
  - `window.cancelAnimationFrame`
  - `resume`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `readonly (from vue)`
### `loop(timestamp: DOMHighResTimeStamp): void`

<details><summary>Code</summary>

```ts
function loop(timestamp: DOMHighResTimeStamp) {
    if (!isActive.value || !window)
      return

    if (!previousFrameTimestamp)
      previousFrameTimestamp = timestamp

    const delta = timestamp - previousFrameTimestamp

    if (intervalLimit.value && delta < intervalLimit.value) {
      rafId = window.requestAnimationFrame(loop)
      return
    }

    previousFrameTimestamp = timestamp
    fn({ delta, timestamp })
    if (once) {
      isActive.value = false
      rafId = null
      return
    }
    rafId = window.requestAnimationFrame(loop)
  }
```
</details>

- **Parameters**:
  - `timestamp: DOMHighResTimeStamp`
- **Return Type**: `void`
- **Calls**:
  - `window.requestAnimationFrame`
  - `fn`
### `resume(): void`

<details><summary>Code</summary>

```ts
function resume() {
    if (!isActive.value && window) {
      isActive.value = true
      previousFrameTimestamp = 0
      rafId = window.requestAnimationFrame(loop)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `window.requestAnimationFrame`
### `pause(): void`

<details><summary>Code</summary>

```ts
function pause() {
    isActive.value = false
    if (rafId != null && window) {
      window.cancelAnimationFrame(rafId)
      rafId = null
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `window.cancelAnimationFrame`

---

## Interfaces

### `UseRafFnCallbackArguments`

<details><summary>Interface Code</summary>

```ts
export interface UseRafFnCallbackArguments {
  /**
   * Time elapsed between this and the last frame.
   */
  delta: number

  /**
   * Time elapsed since the creation of the web page. See {@link https://developer.mozilla.org/en-US/docs/Web/API/DOMHighResTimeStamp#the_time_origin Time origin}.
   */
  timestamp: DOMHighResTimeStamp
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `delta` | `number` | ✗ |  |
| `timestamp` | `DOMHighResTimeStamp` | ✗ |  |

### `UseRafFnOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseRafFnOptions extends ConfigurableWindow {
  /**
   * Start the requestAnimationFrame loop immediately on creation
   *
   * @default true
   */
  immediate?: boolean
  /**
   * The maximum frame per second to execute the function.
   * Set to `undefined` to disable the limit.
   *
   * @default undefined
   */
  fpsLimit?: MaybeRefOrGetter<number>
  /**
   * After the requestAnimationFrame loop executed once, it will be automatically stopped.
   *
   * @default false
   */
  once?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |
| `fpsLimit` | `MaybeRefOrGetter<number>` | ✓ |  |
| `once` | `boolean` | ✓ |  |


---