[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/useIntervalFn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Fn` | `../utils` |
| `Pausable` | `../utils` |
| `isRef` | `vue` |
| `shallowReadonly` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `tryOnScopeDispose` | `../tryOnScopeDispose` |
| `isClient` | `../utils` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `timer` | `ReturnType<typeof setInterval> | null` | let/var | `null` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useIntervalFn(cb: Fn, interval: MaybeRefOrGetter<number>, options: UseIntervalFnOptions): UseIntervalFnReturn`

<details><summary>Code</summary>

```ts
export function useIntervalFn(cb: Fn, interval: MaybeRefOrGetter<number> = 1000, options: UseIntervalFnOptions = {}): UseIntervalFnReturn {
  const {
    immediate = true,
    immediateCallback = false,
  } = options

  let timer: ReturnType<typeof setInterval> | null = null
  const isActive = shallowRef(false)

  function clean() {
    if (timer) {
      clearInterval(timer)
      timer = null
    }
  }

  function pause() {
    isActive.value = false
    clean()
  }

  function resume() {
    const intervalValue = toValue(interval)
    if (intervalValue <= 0)
      return
    isActive.value = true
    if (immediateCallback)
      cb()
    clean()
    if (isActive.value)
      timer = setInterval(cb, intervalValue)
  }

  if (immediate && isClient)
    resume()

  if (isRef(interval) || typeof interval === 'function') {
    const stopWatch = watch(interval, () => {
      if (isActive.value && isClient)
        resume()
    })
    tryOnScopeDispose(stopWatch)
  }

  tryOnScopeDispose(pause)

  return {
    isActive: shallowReadonly(isActive),
    pause,
    resume,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Wrapper for `setInterval` with controls
 *
 * @param cb
 * @param interval
 * @param options
 */
```

- **Parameters**:
  - `cb: Fn`
  - `interval: MaybeRefOrGetter<number>`
  - `options: UseIntervalFnOptions`
- **Return Type**: `UseIntervalFnReturn`
- **Calls**:
  - `shallowRef (from vue)`
  - `clearInterval`
  - `clean`
  - `toValue (from vue)`
  - `cb`
  - `setInterval`
  - `resume`
  - `isRef (from vue)`
  - `watch (from vue)`
  - `tryOnScopeDispose (from ../tryOnScopeDispose)`
  - `shallowReadonly (from vue)`
### `clean(): void`

<details><summary>Code</summary>

```ts
function clean() {
    if (timer) {
      clearInterval(timer)
      timer = null
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clearInterval`
### `pause(): void`

<details><summary>Code</summary>

```ts
function pause() {
    isActive.value = false
    clean()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clean`
### `resume(): void`

<details><summary>Code</summary>

```ts
function resume() {
    const intervalValue = toValue(interval)
    if (intervalValue <= 0)
      return
    isActive.value = true
    if (immediateCallback)
      cb()
    clean()
    if (isActive.value)
      timer = setInterval(cb, intervalValue)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `cb`
  - `clean`
  - `setInterval`

---

## Interfaces

### `UseIntervalFnOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseIntervalFnOptions {
  /**
   * Start the timer immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Execute the callback immediately after calling `resume`
   *
   * @default false
   */
  immediateCallback?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |
| `immediateCallback` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseIntervalFnReturn`

```ts
type UseIntervalFnReturn = Pausable;
```


---