[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 5 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useIdle/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableEventFilter` | `@vueuse/shared` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `WindowEventName` | `../useEventListener` |
| `createFilterWrapper` | `@vueuse/shared` |
| `throttleFilter` | `@vueuse/shared` |
| `timestamp` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `defaultEvents` | `WindowEventName[]` | const | `['mousemove', 'mousedown', 'resize', 'keydown', 'touchstart', 'wheel']` | ✗ |
| `oneMinute` | `60000` | const | `60_000` | ✗ |
| `timer` | `any` | let/var | `*not shown*` | ✗ |
| `document` | `Document` | const | `window.document` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Functions

### `useIdle(timeout: number, options: UseIdleOptions): UseIdleReturn`

<details><summary>Code</summary>

```ts
export function useIdle(
  timeout: number = oneMinute,
  options: UseIdleOptions = {},
): UseIdleReturn {
  const {
    initialState = false,
    listenForVisibilityChange = true,
    events = defaultEvents,
    window = defaultWindow,
    eventFilter = throttleFilter(50),
  } = options
  const idle = shallowRef(initialState)
  const lastActive = shallowRef(timestamp())

  let timer: any

  const reset = () => {
    idle.value = false
    clearTimeout(timer)
    timer = setTimeout(() => idle.value = true, timeout)
  }

  const onEvent = createFilterWrapper(
    eventFilter,
    () => {
      lastActive.value = timestamp()
      reset()
    },
  )

  if (window) {
    const document = window.document
    const listenerOptions = { passive: true }

    for (const event of events)
      useEventListener(window, event, onEvent, listenerOptions)

    if (listenForVisibilityChange) {
      useEventListener(document, 'visibilitychange', () => {
        if (!document.hidden)
          onEvent()
      }, listenerOptions)
    }

    reset()
  }

  return {
    idle,
    lastActive,
    reset,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Tracks whether the user is being inactive.
 *
 * @see https://vueuse.org/useIdle
 * @param timeout default to 1 minute
 * @param options IdleOptions
 */
```

- **Parameters**:
  - `timeout: number`
  - `options: UseIdleOptions`
- **Return Type**: `UseIdleReturn`
- **Calls**:
  - `throttleFilter (from @vueuse/shared)`
  - `shallowRef (from vue)`
  - `timestamp (from @vueuse/shared)`
  - `clearTimeout`
  - `setTimeout`
  - `createFilterWrapper (from @vueuse/shared)`
  - `reset`
  - `useEventListener (from ../useEventListener)`
  - `onEvent`
### `reset(): void`

<details><summary>Code</summary>

```ts
() => {
    idle.value = false
    clearTimeout(timer)
    timer = setTimeout(() => idle.value = true, timeout)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clearTimeout`
  - `setTimeout`

---

## Interfaces

### `UseIdleOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseIdleOptions extends ConfigurableWindow, ConfigurableEventFilter {
  /**
   * Event names that listen to for detected user activity
   *
   * @default ['mousemove', 'mousedown', 'resize', 'keydown', 'touchstart', 'wheel']
   */
  events?: WindowEventName[]
  /**
   * Listen for document visibility change
   *
   * @default true
   */
  listenForVisibilityChange?: boolean
  /**
   * Initial state of the ref idle
   *
   * @default false
   */
  initialState?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `events` | `WindowEventName[]` | ✓ |  |
| `listenForVisibilityChange` | `boolean` | ✓ |  |
| `initialState` | `boolean` | ✓ |  |

### `UseIdleReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseIdleReturn {
  idle: ShallowRef<boolean>
  lastActive: ShallowRef<number>
  reset: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `idle` | `ShallowRef<boolean>` | ✗ |  |
| `lastActive` | `ShallowRef<number>` | ✗ |  |
| `reset` | `() => void` | ✗ |  |


---