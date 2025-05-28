[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
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
📂 **`packages/shared/useTimeoutFn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `AnyFn` | `../utils` |
| `Stoppable` | `../utils` |
| `shallowReadonly` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `tryOnScopeDispose` | `../tryOnScopeDispose` |
| `isClient` | `../utils` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `timer` | `ReturnType<typeof setTimeout> | null` | let/var | `null` | ✗ |


---

## Functions

### `useTimeoutFn(cb: CallbackFn, interval: MaybeRefOrGetter<number>, options: UseTimeoutFnOptions): UseTimeoutFnReturn<CallbackFn>`

<details><summary>Code</summary>

```ts
export function useTimeoutFn<CallbackFn extends AnyFn>(
  cb: CallbackFn,
  interval: MaybeRefOrGetter<number>,
  options: UseTimeoutFnOptions = {},
): UseTimeoutFnReturn<CallbackFn> {
  const {
    immediate = true,
    immediateCallback = false,
  } = options

  const isPending = shallowRef(false)

  let timer: ReturnType<typeof setTimeout> | null = null

  function clear() {
    if (timer) {
      clearTimeout(timer)
      timer = null
    }
  }

  function stop() {
    isPending.value = false
    clear()
  }

  function start(...args: Parameters<CallbackFn> | []) {
    if (immediateCallback)
      cb()
    clear()
    isPending.value = true
    timer = setTimeout(() => {
      isPending.value = false
      timer = null

      cb(...args)
    }, toValue(interval))
  }

  if (immediate) {
    isPending.value = true
    if (isClient)
      start()
  }

  tryOnScopeDispose(stop)

  return {
    isPending: shallowReadonly(isPending),
    start,
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Wrapper for `setTimeout` with controls.
 *
 * @param cb
 * @param interval
 * @param options
 */
```

- **Parameters**:
  - `cb: CallbackFn`
  - `interval: MaybeRefOrGetter<number>`
  - `options: UseTimeoutFnOptions`
- **Return Type**: `UseTimeoutFnReturn<CallbackFn>`
- **Calls**:
  - `shallowRef (from vue)`
  - `clearTimeout`
  - `clear`
  - `cb`
  - `setTimeout`
  - `toValue (from vue)`
  - `start`
  - `tryOnScopeDispose (from ../tryOnScopeDispose)`
  - `shallowReadonly (from vue)`
### `clear(): void`

<details><summary>Code</summary>

```ts
function clear() {
    if (timer) {
      clearTimeout(timer)
      timer = null
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clearTimeout`
### `stop(): void`

<details><summary>Code</summary>

```ts
function stop() {
    isPending.value = false
    clear()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clear`
### `start(args: Parameters<CallbackFn> | []): void`

<details><summary>Code</summary>

```ts
function start(...args: Parameters<CallbackFn> | []) {
    if (immediateCallback)
      cb()
    clear()
    isPending.value = true
    timer = setTimeout(() => {
      isPending.value = false
      timer = null

      cb(...args)
    }, toValue(interval))
  }
```
</details>

- **Parameters**:
  - `args: Parameters<CallbackFn> | []`
- **Return Type**: `void`
- **Calls**:
  - `cb`
  - `clear`
  - `setTimeout`
  - `toValue (from vue)`

---

## Interfaces

### `UseTimeoutFnOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseTimeoutFnOptions {
  /**
   * Start the timer immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Execute the callback immediately after calling `start`
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

### `UseTimeoutFnReturn<CallbackFn extends AnyFn extends AnyFn>`

```ts
type UseTimeoutFnReturn<CallbackFn extends AnyFn extends AnyFn> = Stoppable<Parameters<CallbackFn> | []>;
```


---