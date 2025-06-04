[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 7 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 6 |
| ⚡ Async/Await Patterns | 4 |
| 🟢 Vue Composition API | 4 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useFullscreen/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableDocument` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `tryOnMounted` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `defaultDocument` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `eventHandlers` | `"fullscreenchange"[]` | const | `[
  'fullscreenchange',
  'webkitfullscreenchange',
  'webkitendfullscreen',
  'mozfullscreenchange',
  'MSFullscreenChange',
] as any as 'fullscreenchange'[]` | ✗ |
| `fullscreenElementMethod` | `"fullscreenElement"` | const | `[
    'fullscreenElement',
    'webkitFullscreenElement',
    'mozFullScreenElement',
    'msFullscreenElement',
  ].find(m => (document && m in document)) as 'fullscreenElement' | undefined` | ✗ |
| `target` | `any` | const | `targetRef.value` | ✗ |
| `target` | `any` | let/var | `targetRef.value` | ✗ |
| `target` | `any` | let/var | `targetRef.value` | ✗ |
| `listenerOptions` | `{ capture: boolean; passive: boolean; }` | const | `{ capture: false, passive: true }` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useFullscreen` | document[exitMethod.value](), target[exitMethod.value](), exit(), target[requestMethod.value](), (isFullscreen.value ? exit() : enter()) | *none* |
| async-function | `exit` | document[exitMethod.value](), target[exitMethod.value]() | *none* |
| async-function | `enter` | exit(), target[requestMethod.value]() | *none* |
| async-function | `toggle` | (isFullscreen.value ? exit() : enter()) | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useFullscreen(target: MaybeElementRef, options: UseFullscreenOptions): { isSupported: any; isFullscreen: any; enter: () => Promise<void>; exit: () => Promise<void>; toggle: () => Promise<void>; }`

<details><summary>Code</summary>

```ts
export function useFullscreen(
  target?: MaybeElementRef,
  options: UseFullscreenOptions = {},
) {
  const {
    document = defaultDocument,
    autoExit = false,
  } = options

  const targetRef = computed(() => unrefElement(target) ?? document?.documentElement)
  const isFullscreen = shallowRef(false)

  const requestMethod = computed<'requestFullscreen' | undefined>(() => {
    return [
      'requestFullscreen',
      'webkitRequestFullscreen',
      'webkitEnterFullscreen',
      'webkitEnterFullScreen',
      'webkitRequestFullScreen',
      'mozRequestFullScreen',
      'msRequestFullscreen',
    ].find(m => (document && m in document) || (targetRef.value && m in targetRef.value)) as any
  })

  const exitMethod = computed<'exitFullscreen' | undefined>(() => {
    return [
      'exitFullscreen',
      'webkitExitFullscreen',
      'webkitExitFullScreen',
      'webkitCancelFullScreen',
      'mozCancelFullScreen',
      'msExitFullscreen',
    ].find(m => (document && m in document) || (targetRef.value && m in targetRef.value)) as any
  })

  const fullscreenEnabled = computed<'fullscreenEnabled' | undefined>(() => {
    return [
      'fullScreen',
      'webkitIsFullScreen',
      'webkitDisplayingFullscreen',
      'mozFullScreen',
      'msFullscreenElement',
    ].find(m => (document && m in document) || (targetRef.value && m in targetRef.value)) as any
  })

  const fullscreenElementMethod = [
    'fullscreenElement',
    'webkitFullscreenElement',
    'mozFullScreenElement',
    'msFullscreenElement',
  ].find(m => (document && m in document)) as 'fullscreenElement' | undefined

  const isSupported = useSupported(() =>
    targetRef.value
    && document
    && requestMethod.value !== undefined
    && exitMethod.value !== undefined
    && fullscreenEnabled.value !== undefined)

  const isCurrentElementFullScreen = (): boolean => {
    if (fullscreenElementMethod)
      return document?.[fullscreenElementMethod] === targetRef.value
    return false
  }

  const isElementFullScreen = (): boolean => {
    if (fullscreenEnabled.value) {
      if (document && document[fullscreenEnabled.value] != null) {
        return document[fullscreenEnabled.value]
      }
      else {
        const target = targetRef.value
        // @ts-expect-error - Fallback for WebKit and iOS Safari browsers
        if (target?.[fullscreenEnabled.value] != null) {
          // @ts-expect-error - Fallback for WebKit and iOS Safari browsers
          return Boolean(target[fullscreenEnabled.value])
        }
      }
    }
    return false
  }

  async function exit() {
    if (!isSupported.value || !isFullscreen.value)
      return
    if (exitMethod.value) {
      if (document?.[exitMethod.value] != null) {
        await document[exitMethod.value]()
      }
      else {
        const target = targetRef.value
        // @ts-expect-error - Fallback for Safari iOS
        if (target?.[exitMethod.value] != null)
          // @ts-expect-error - Fallback for Safari iOS
          await target[exitMethod.value]()
      }
    }

    isFullscreen.value = false
  }

  async function enter() {
    if (!isSupported.value || isFullscreen.value)
      return

    if (isElementFullScreen())
      await exit()

    const target = targetRef.value
    if (requestMethod.value && target?.[requestMethod.value] != null) {
      await target[requestMethod.value]()
      isFullscreen.value = true
    }
  }

  async function toggle() {
    await (isFullscreen.value ? exit() : enter())
  }

  const handlerCallback = () => {
    const isElementFullScreenValue = isElementFullScreen()
    if (!isElementFullScreenValue || (isElementFullScreenValue && isCurrentElementFullScreen()))
      isFullscreen.value = isElementFullScreenValue
  }

  const listenerOptions = { capture: false, passive: true }
  useEventListener(document, eventHandlers, handlerCallback, listenerOptions)
  useEventListener(() => unrefElement(targetRef), eventHandlers, handlerCallback, listenerOptions)

  tryOnMounted(handlerCallback, false)

  if (autoExit)
    tryOnScopeDispose(exit)

  return {
    isSupported,
    isFullscreen,
    enter,
    exit,
    toggle,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Fullscreen API.
 *
 * @see https://vueuse.org/useFullscreen
 * @param target
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `options: UseFullscreenOptions`
- **Return Type**: `{ isSupported: any; isFullscreen: any; enter: () => Promise<void>; exit: () => Promise<void>; toggle: () => Promise<void>; }`
- **Calls**:
  - `computed (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `shallowRef (from vue)`
  - `[
      'requestFullscreen',
      'webkitRequestFullscreen',
      'webkitEnterFullscreen',
      'webkitEnterFullScreen',
      'webkitRequestFullScreen',
      'mozRequestFullScreen',
      'msRequestFullscreen',
    ].find`
  - `[
      'exitFullscreen',
      'webkitExitFullscreen',
      'webkitExitFullScreen',
      'webkitCancelFullScreen',
      'mozCancelFullScreen',
      'msExitFullscreen',
    ].find`
  - `[
      'fullScreen',
      'webkitIsFullScreen',
      'webkitDisplayingFullscreen',
      'mozFullScreen',
      'msFullscreenElement',
    ].find`
  - `[
    'fullscreenElement',
    'webkitFullscreenElement',
    'mozFullScreenElement',
    'msFullscreenElement',
  ].find`
  - `useSupported (from ../useSupported)`
  - `Boolean`
  - `complex_call_3670`
  - `complex_call_3933`
  - `isElementFullScreen`
  - `exit`
  - `complex_call_4272`
  - `enter`
  - `isCurrentElementFullScreen`
  - `useEventListener (from ../useEventListener)`
  - `tryOnMounted (from @vueuse/shared)`
  - `tryOnScopeDispose (from @vueuse/shared)`
- **Internal Comments**:
```
// @ts-expect-error - Fallback for WebKit and iOS Safari browsers (x2)
// @ts-expect-error - Fallback for Safari iOS (x3)
```

### `isCurrentElementFullScreen(): boolean`

<details><summary>Code</summary>

```ts
(): boolean => {
    if (fullscreenElementMethod)
      return document?.[fullscreenElementMethod] === targetRef.value
    return false
  }
```
</details>

- **Return Type**: `boolean`
### `isElementFullScreen(): boolean`

<details><summary>Code</summary>

```ts
(): boolean => {
    if (fullscreenEnabled.value) {
      if (document && document[fullscreenEnabled.value] != null) {
        return document[fullscreenEnabled.value]
      }
      else {
        const target = targetRef.value
        // @ts-expect-error - Fallback for WebKit and iOS Safari browsers
        if (target?.[fullscreenEnabled.value] != null) {
          // @ts-expect-error - Fallback for WebKit and iOS Safari browsers
          return Boolean(target[fullscreenEnabled.value])
        }
      }
    }
    return false
  }
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `Boolean`
- **Internal Comments**:
```
// @ts-expect-error - Fallback for WebKit and iOS Safari browsers (x2)
```

### `exit(): Promise<void>`

<details><summary>Code</summary>

```ts
async function exit() {
    if (!isSupported.value || !isFullscreen.value)
      return
    if (exitMethod.value) {
      if (document?.[exitMethod.value] != null) {
        await document[exitMethod.value]()
      }
      else {
        const target = targetRef.value
        // @ts-expect-error - Fallback for Safari iOS
        if (target?.[exitMethod.value] != null)
          // @ts-expect-error - Fallback for Safari iOS
          await target[exitMethod.value]()
      }
    }

    isFullscreen.value = false
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `complex_call_3670`
  - `complex_call_3933`
- **Internal Comments**:
```
// @ts-expect-error - Fallback for Safari iOS (x3)
```

### `enter(): Promise<void>`

<details><summary>Code</summary>

```ts
async function enter() {
    if (!isSupported.value || isFullscreen.value)
      return

    if (isElementFullScreen())
      await exit()

    const target = targetRef.value
    if (requestMethod.value && target?.[requestMethod.value] != null) {
      await target[requestMethod.value]()
      isFullscreen.value = true
    }
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `isElementFullScreen`
  - `exit`
  - `complex_call_4272`
### `toggle(): Promise<void>`

<details><summary>Code</summary>

```ts
async function toggle() {
    await (isFullscreen.value ? exit() : enter())
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `exit`
  - `enter`
### `handlerCallback(): void`

<details><summary>Code</summary>

```ts
() => {
    const isElementFullScreenValue = isElementFullScreen()
    if (!isElementFullScreenValue || (isElementFullScreenValue && isCurrentElementFullScreen()))
      isFullscreen.value = isElementFullScreenValue
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `isElementFullScreen`
  - `isCurrentElementFullScreen`

---

## Interfaces

### `UseFullscreenOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFullscreenOptions extends ConfigurableDocument {
  /**
   * Automatically exit fullscreen when component is unmounted
   *
   * @default false
   */
  autoExit?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `autoExit` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseFullscreenReturn`

```ts
type UseFullscreenReturn = ReturnType<typeof useFullscreen>;
```


---