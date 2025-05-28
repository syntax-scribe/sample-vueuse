[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 12 |
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
📂 **`packages/core/onLongPress/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Position` | `../types` |
| `MaybeElementRef` | `../unrefElement` |
| `computed` | `vue` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `DEFAULT_DELAY` | `500` | const | `500` | ✗ |
| `DEFAULT_THRESHOLD` | `10` | const | `10` | ✗ |
| `timeout` | `ReturnType<typeof setTimeout> | undefined` | let/var | `*not shown*` | ✗ |
| `posStart` | `Position | undefined` | let/var | `*not shown*` | ✗ |
| `startTimestamp` | `number | undefined` | let/var | `*not shown*` | ✗ |
| `hasLongPressed` | `boolean` | let/var | `false` | ✗ |
| `dx` | `number` | const | `ev.x - _posStart.x` | ✗ |
| `dy` | `number` | const | `ev.y - _posStart.y` | ✗ |
| `dx` | `number` | const | `ev.x - posStart.x` | ✗ |
| `dy` | `number` | const | `ev.y - posStart.y` | ✗ |
| `listenerOptions` | `AddEventListenerOptions` | const | `{
    capture: options?.modifiers?.capture,
    once: options?.modifiers?.once,
  }` | ✗ |
| `cleanup` | `(() => void)[]` | const | `[
    useEventListener(elementRef, 'pointerdown', onDown, listenerOptions),
    useEventListener(elementRef, 'pointermove', onMove, listenerOptions),
    useEventListener(elementRef, ['pointerup', 'pointerleave'], onRelease, listenerOptions),
  ]` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `onLongPress(target: MaybeElementRef, handler: (evt: PointerEvent) => void, options: OnLongPressOptions): () => void`

<details><summary>Code</summary>

```ts
export function onLongPress(
  target: MaybeElementRef,
  handler: (evt: PointerEvent) => void,
  options?: OnLongPressOptions,
) {
  const elementRef = computed(() => unrefElement(target))

  let timeout: ReturnType<typeof setTimeout> | undefined
  let posStart: Position | undefined
  let startTimestamp: number | undefined
  let hasLongPressed = false

  function clear() {
    if (timeout) {
      clearTimeout(timeout)
      timeout = undefined
    }
    posStart = undefined
    startTimestamp = undefined
    hasLongPressed = false
  }

  function onRelease(ev: PointerEvent) {
    const [_startTimestamp, _posStart, _hasLongPressed] = [startTimestamp, posStart, hasLongPressed]
    clear()

    if (!options?.onMouseUp || !_posStart || !_startTimestamp)
      return

    if (options?.modifiers?.self && ev.target !== elementRef.value)
      return

    if (options?.modifiers?.prevent)
      ev.preventDefault()

    if (options?.modifiers?.stop)
      ev.stopPropagation()

    const dx = ev.x - _posStart.x
    const dy = ev.y - _posStart.y
    const distance = Math.sqrt(dx * dx + dy * dy)
    options.onMouseUp(ev.timeStamp - _startTimestamp, distance, _hasLongPressed)
  }

  function onDown(ev: PointerEvent) {
    if (options?.modifiers?.self && ev.target !== elementRef.value)
      return

    clear()

    if (options?.modifiers?.prevent)
      ev.preventDefault()

    if (options?.modifiers?.stop)
      ev.stopPropagation()

    posStart = {
      x: ev.x,
      y: ev.y,
    }
    startTimestamp = ev.timeStamp
    timeout = setTimeout(
      () => {
        hasLongPressed = true
        handler(ev)
      },
      options?.delay ?? DEFAULT_DELAY,
    )
  }

  function onMove(ev: PointerEvent) {
    if (options?.modifiers?.self && ev.target !== elementRef.value)
      return

    if (!posStart || options?.distanceThreshold === false)
      return

    if (options?.modifiers?.prevent)
      ev.preventDefault()

    if (options?.modifiers?.stop)
      ev.stopPropagation()

    const dx = ev.x - posStart.x
    const dy = ev.y - posStart.y
    const distance = Math.sqrt(dx * dx + dy * dy)
    if (distance >= (options?.distanceThreshold ?? DEFAULT_THRESHOLD))
      clear()
  }

  const listenerOptions: AddEventListenerOptions = {
    capture: options?.modifiers?.capture,
    once: options?.modifiers?.once,
  }

  const cleanup = [
    useEventListener(elementRef, 'pointerdown', onDown, listenerOptions),
    useEventListener(elementRef, 'pointermove', onMove, listenerOptions),
    useEventListener(elementRef, ['pointerup', 'pointerleave'], onRelease, listenerOptions),
  ]

  const stop = () => cleanup.forEach(fn => fn())

  return stop
}
```
</details>

- **Parameters**:
  - `target: MaybeElementRef`
  - `handler: (evt: PointerEvent) => void`
  - `options: OnLongPressOptions`
- **Return Type**: `() => void`
- **Calls**:
  - `computed (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `clearTimeout`
  - `clear`
  - `ev.preventDefault`
  - `ev.stopPropagation`
  - `Math.sqrt`
  - `options.onMouseUp`
  - `setTimeout`
  - `handler`
  - `useEventListener (from ../useEventListener)`
  - `cleanup.forEach`
  - `fn`
### `clear(): void`

<details><summary>Code</summary>

```ts
function clear() {
    if (timeout) {
      clearTimeout(timeout)
      timeout = undefined
    }
    posStart = undefined
    startTimestamp = undefined
    hasLongPressed = false
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clearTimeout`
### `onRelease(ev: PointerEvent): void`

<details><summary>Code</summary>

```ts
function onRelease(ev: PointerEvent) {
    const [_startTimestamp, _posStart, _hasLongPressed] = [startTimestamp, posStart, hasLongPressed]
    clear()

    if (!options?.onMouseUp || !_posStart || !_startTimestamp)
      return

    if (options?.modifiers?.self && ev.target !== elementRef.value)
      return

    if (options?.modifiers?.prevent)
      ev.preventDefault()

    if (options?.modifiers?.stop)
      ev.stopPropagation()

    const dx = ev.x - _posStart.x
    const dy = ev.y - _posStart.y
    const distance = Math.sqrt(dx * dx + dy * dy)
    options.onMouseUp(ev.timeStamp - _startTimestamp, distance, _hasLongPressed)
  }
```
</details>

- **Parameters**:
  - `ev: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `clear`
  - `ev.preventDefault`
  - `ev.stopPropagation`
  - `Math.sqrt`
  - `options.onMouseUp`
### `onDown(ev: PointerEvent): void`

<details><summary>Code</summary>

```ts
function onDown(ev: PointerEvent) {
    if (options?.modifiers?.self && ev.target !== elementRef.value)
      return

    clear()

    if (options?.modifiers?.prevent)
      ev.preventDefault()

    if (options?.modifiers?.stop)
      ev.stopPropagation()

    posStart = {
      x: ev.x,
      y: ev.y,
    }
    startTimestamp = ev.timeStamp
    timeout = setTimeout(
      () => {
        hasLongPressed = true
        handler(ev)
      },
      options?.delay ?? DEFAULT_DELAY,
    )
  }
```
</details>

- **Parameters**:
  - `ev: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `clear`
  - `ev.preventDefault`
  - `ev.stopPropagation`
  - `setTimeout`
  - `handler`
### `onMove(ev: PointerEvent): void`

<details><summary>Code</summary>

```ts
function onMove(ev: PointerEvent) {
    if (options?.modifiers?.self && ev.target !== elementRef.value)
      return

    if (!posStart || options?.distanceThreshold === false)
      return

    if (options?.modifiers?.prevent)
      ev.preventDefault()

    if (options?.modifiers?.stop)
      ev.stopPropagation()

    const dx = ev.x - posStart.x
    const dy = ev.y - posStart.y
    const distance = Math.sqrt(dx * dx + dy * dy)
    if (distance >= (options?.distanceThreshold ?? DEFAULT_THRESHOLD))
      clear()
  }
```
</details>

- **Parameters**:
  - `ev: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `ev.preventDefault`
  - `ev.stopPropagation`
  - `Math.sqrt`
  - `clear`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => cleanup.forEach(fn => fn())
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `cleanup.forEach`

---

## Interfaces

### `OnLongPressOptions`

<details><summary>Interface Code</summary>

```ts
export interface OnLongPressOptions {
  /**
   * Time in ms till `longpress` gets called
   *
   * @default 500
   */
  delay?: number

  modifiers?: OnLongPressModifiers

  /**
   * Allowance of moving distance in pixels,
   * The action will get canceled When moving too far from the pointerdown position.
   * @default 10
   */
  distanceThreshold?: number | false

  /**
   * Function called when the ref element is released.
   * @param duration how long the element was pressed in ms
   * @param distance distance from the pointerdown position
   * @param isLongPress whether the action was a long press or not
   */
  onMouseUp?: (duration: number, distance: number, isLongPress: boolean) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `delay` | `number` | ✓ |  |
| `modifiers` | `OnLongPressModifiers` | ✓ |  |
| `distanceThreshold` | `number | false` | ✓ |  |
| `onMouseUp` | `(duration: number, distance: number, isLongPress: boolean) => void` | ✓ |  |

### `OnLongPressModifiers`

<details><summary>Interface Code</summary>

```ts
export interface OnLongPressModifiers {
  stop?: boolean
  once?: boolean
  prevent?: boolean
  capture?: boolean
  self?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `stop` | `boolean` | ✓ |  |
| `once` | `boolean` | ✓ |  |
| `prevent` | `boolean` | ✓ |  |
| `capture` | `boolean` | ✓ |  |
| `self` | `boolean` | ✓ |  |


---