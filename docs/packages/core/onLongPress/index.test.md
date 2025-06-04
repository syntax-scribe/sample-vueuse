[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 9 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 7 |
| ⚡ Async/Await Patterns | 8 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/onLongPress/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `shallowRef` | `vue` |
| `useEventListener` | `../useEventListener` |
| `onLongPress` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `element` | `Ref<HTMLElement>` | let/var | `*not shown*` | ✗ |
| `parentElement` | `Ref<HTMLElement>` | let/var | `*not shown*` | ✗ |
| `childElement` | `Ref<HTMLElement>` | let/var | `*not shown*` | ✗ |
| `pointerdownEvent` | `PointerEvent` | let/var | `*not shown*` | ✗ |
| `pointerUpEvent` | `PointerEvent` | let/var | `*not shown*` | ✗ |
| `moveWithinThresholdEvent` | `PointerEvent` | let/var | `new PointerEvent('pointermove', { cancelable: true, bubbles: true, clientX: 17, clientY: 25 })` | ✗ |
| `moveOutsideThresholdEvent` | `PointerEvent` | let/var | `new PointerEvent('pointermove', { cancelable: true, bubbles: true, clientX: 4, clientY: 30 })` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `triggerCallback` | vi.advanceTimersByTimeAsync(500) | *none* |
| async-function | `triggerCallbackWithDelay` | vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(1000) | *none* |
| async-function | `notTriggerCallbackOnChildLongPress` | vi.advanceTimersByTimeAsync(500) | *none* |
| async-function | `workOnceAndPreventModifiers` | vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500) | *none* |
| async-function | `stopPropagation` | vi.advanceTimersByTimeAsync(500) | *none* |
| async-function | `stopEventListeners` | vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500) | *none* |
| async-function | `triggerCallbackWithThreshold` | vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500) | *none* |
| async-function | `triggerOnMouseUp` | vi.advanceTimersByTimeAsync(250), vi.advanceTimersByTimeAsync(500), vi.advanceTimersByTimeAsync(500) | *none* |


---

## Functions

### `triggerCallback(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function triggerCallback(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    onLongPress(isRef ? element : element.value, onLongPressCallback)
    element.value.dispatchEvent(pointerdownEvent)
    expect(onLongPressCallback).toHaveBeenCalledTimes(0)
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(1)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `onLongPress (from ./index)`
  - `element.value.dispatchEvent`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
  - `vi.advanceTimersByTimeAsync`
### `triggerCallbackWithDelay(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function triggerCallbackWithDelay(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    onLongPress(isRef ? element : element.value, onLongPressCallback, { delay: 1000 })
    // first pointer down
    element.value.dispatchEvent(pointerdownEvent)

    // wait for 500ms after pointer down
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(0)

    // pointer up to cancel callback
    element.value.dispatchEvent(pointerUpEvent)

    // wait for 500ms after pointer up
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(0)

    // another pointer down
    element.value.dispatchEvent(pointerdownEvent)

    // wait for 1000ms after pointer down
    await vi.advanceTimersByTimeAsync(1000)
    expect(onLongPressCallback).toHaveBeenCalledTimes(1)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `onLongPress (from ./index)`
  - `element.value.dispatchEvent`
  - `vi.advanceTimersByTimeAsync`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
- **Internal Comments**:
```
// first pointer down (x5)
// wait for 500ms after pointer down (x2)
// pointer up to cancel callback (x5)
// wait for 500ms after pointer up (x2)
// another pointer down (x5)
// wait for 1000ms after pointer down (x2)
```

### `notTriggerCallbackOnChildLongPress(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function notTriggerCallbackOnChildLongPress(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    onLongPress(isRef ? element : element.value, onLongPressCallback, { modifiers: { self: true } })

    childElement.value.dispatchEvent(pointerdownEvent)

    await vi.advanceTimersByTimeAsync(500)

    expect(onLongPressCallback).toHaveBeenCalledTimes(0)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `onLongPress (from ./index)`
  - `childElement.value.dispatchEvent`
  - `vi.advanceTimersByTimeAsync`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
### `workOnceAndPreventModifiers(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function workOnceAndPreventModifiers(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    onLongPress(isRef ? element : element.value, onLongPressCallback, { modifiers: { once: true, prevent: true } })

    element.value.dispatchEvent(pointerdownEvent)

    await vi.advanceTimersByTimeAsync(500)

    expect(onLongPressCallback).toHaveBeenCalledTimes(1)
    expect(pointerdownEvent.defaultPrevented).toBe(true)

    await vi.advanceTimersByTimeAsync(500)

    expect(onLongPressCallback).toHaveBeenCalledTimes(1)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `onLongPress (from ./index)`
  - `element.value.dispatchEvent`
  - `vi.advanceTimersByTimeAsync`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
  - `expect(pointerdownEvent.defaultPrevented).toBe`
### `stopPropagation(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function stopPropagation(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    const onParentLongPressCallback = vi.fn()
    useEventListener(parentElement, 'pointerdown', onParentLongPressCallback)
    onLongPress(isRef ? element : element.value, onLongPressCallback, { modifiers: { stop: true } })

    element.value.dispatchEvent(pointerdownEvent)

    await vi.advanceTimersByTimeAsync(500)

    expect(onLongPressCallback).toHaveBeenCalledTimes(1)
    expect(onParentLongPressCallback).toHaveBeenCalledTimes(0)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `useEventListener (from ../useEventListener)`
  - `onLongPress (from ./index)`
  - `element.value.dispatchEvent`
  - `vi.advanceTimersByTimeAsync`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
  - `expect(onParentLongPressCallback).toHaveBeenCalledTimes`
### `stopEventListeners(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function stopEventListeners(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    const stop = onLongPress(isRef ? element : element.value, onLongPressCallback, { modifiers: { stop: true } })

    // before calling stop, the callback should be called
    element.value.dispatchEvent(pointerdownEvent)

    await vi.advanceTimersByTimeAsync(500)

    expect(onLongPressCallback).toHaveBeenCalledTimes(1)

    stop()

    // before calling stop, the callback should no longer be called
    onLongPressCallback.mockClear()

    element.value.dispatchEvent(pointerdownEvent)

    await vi.advanceTimersByTimeAsync(500)

    expect(onLongPressCallback).toHaveBeenCalledTimes(0)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `onLongPress (from ./index)`
  - `element.value.dispatchEvent`
  - `vi.advanceTimersByTimeAsync`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
  - `stop`
  - `onLongPressCallback.mockClear`
- **Internal Comments**:
```
// before calling stop, the callback should be called (x5)
// before calling stop, the callback should no longer be called (x4)
```

### `triggerCallbackWithThreshold(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function triggerCallbackWithThreshold(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    pointerdownEvent = new PointerEvent('pointerdown', { cancelable: true, bubbles: true, clientX: 20, clientY: 20 })
    const moveWithinThresholdEvent = new PointerEvent('pointermove', { cancelable: true, bubbles: true, clientX: 17, clientY: 25 })
    const moveOutsideThresholdEvent = new PointerEvent('pointermove', { cancelable: true, bubbles: true, clientX: 4, clientY: 30 })
    onLongPress(isRef ? element : element.value, onLongPressCallback, { distanceThreshold: 15, delay: 1000 })
    // first pointer down
    element.value.dispatchEvent(pointerdownEvent)

    // pointer move outside threshold
    await vi.advanceTimersByTimeAsync(500)
    element.value.dispatchEvent(moveOutsideThresholdEvent)
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(0)

    // pointer up to cancel callback
    element.value.dispatchEvent(pointerUpEvent)

    // wait for 500ms after pointer up
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(0)

    // another pointer down
    element.value.dispatchEvent(pointerdownEvent)

    // pointer move within threshold
    await vi.advanceTimersByTimeAsync(500)
    element.value.dispatchEvent(moveWithinThresholdEvent)
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(1)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `onLongPress (from ./index)`
  - `element.value.dispatchEvent`
  - `vi.advanceTimersByTimeAsync`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
- **Internal Comments**:
```
// first pointer down (x5)
// pointer move outside threshold (x2)
// pointer up to cancel callback (x5)
// wait for 500ms after pointer up (x2)
// another pointer down (x5)
// pointer move within threshold (x2)
```

### `triggerOnMouseUp(isRef: boolean): Promise<void>`

<details><summary>Code</summary>

```ts
async function triggerOnMouseUp(isRef: boolean) {
    const onLongPressCallback = vi.fn()
    const onMouseUpCallback = vi.fn()
    onLongPress(isRef ? element : element.value, onLongPressCallback, { onMouseUp: onMouseUpCallback })

    // first pointer down
    pointerdownEvent = new PointerEvent('pointerdown', { cancelable: true, bubbles: true })
    element.value.dispatchEvent(pointerdownEvent)

    // wait for 250 after pointer down
    await vi.advanceTimersByTimeAsync(250)
    expect(onLongPressCallback).toHaveBeenCalledTimes(0)
    expect(onMouseUpCallback).toHaveBeenCalledTimes(0)

    // pointer up to cancel callback
    pointerUpEvent = new PointerEvent('pointerup', { cancelable: true, bubbles: true })
    element.value.dispatchEvent(pointerUpEvent)
    expect(onMouseUpCallback).toHaveBeenCalledTimes(1)
    expect(onMouseUpCallback).toBeCalledWith(expect.any(Number), 0, false)
    expect(onMouseUpCallback.mock.calls[0][0]).toBeGreaterThanOrEqual(250 - 2)

    // wait for 500ms after pointer up
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(0)

    // another pointer down
    pointerdownEvent = new PointerEvent('pointerdown', { cancelable: true, bubbles: true })
    element.value.dispatchEvent(pointerdownEvent)

    // wait for 500 after pointer down
    await vi.advanceTimersByTimeAsync(500)
    expect(onLongPressCallback).toHaveBeenCalledTimes(1)
    expect(onMouseUpCallback).toHaveBeenCalledTimes(1)

    pointerUpEvent = new PointerEvent('pointerup', { cancelable: true, bubbles: true })
    element.value.dispatchEvent(pointerUpEvent)
    expect(onMouseUpCallback).toHaveBeenCalledTimes(2)
    expect(onMouseUpCallback).toBeCalledWith(expect.any(Number), 0, true)
    expect(onMouseUpCallback.mock.calls[1][0]).toBeGreaterThanOrEqual(500 - 2)
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.fn`
  - `onLongPress (from ./index)`
  - `element.value.dispatchEvent`
  - `vi.advanceTimersByTimeAsync`
  - `expect(onLongPressCallback).toHaveBeenCalledTimes`
  - `expect(onMouseUpCallback).toHaveBeenCalledTimes`
  - `expect(onMouseUpCallback).toBeCalledWith`
  - `expect.any`
  - `expect(onMouseUpCallback.mock.calls[0][0]).toBeGreaterThanOrEqual`
  - `expect(onMouseUpCallback.mock.calls[1][0]).toBeGreaterThanOrEqual`
- **Internal Comments**:
```
// first pointer down (x3)
// wait for 250 after pointer down (x2)
// pointer up to cancel callback (x3)
// wait for 500ms after pointer up (x2)
// another pointer down (x3)
// wait for 500 after pointer down (x2)
```

### `suites(isRef: boolean): void`

<details><summary>Code</summary>

```ts
function suites(isRef: boolean) {
    describe('given no options', () => {
      it('should trigger longpress after 500ms', () => triggerCallback(isRef))
    })

    describe('given options', () => {
      it('should trigger longpress after options.delay ms', () => triggerCallbackWithDelay(isRef))
      it('should not trigger longpress when child element on longpress', () => notTriggerCallbackOnChildLongPress(isRef))
      it('should work with once and prevent modifiers', () => workOnceAndPreventModifiers(isRef))
      it('should stop propagation', () => stopPropagation(isRef))
      it('should remove event listeners after being stopped', () => stopEventListeners(isRef))
      it('should trigger longpress if pointer is moved', () => triggerCallbackWithThreshold(isRef))
      it('should trigger onMouseUp when pointer is released', () => triggerOnMouseUp(isRef))
    })
  }
```
</details>

- **Parameters**:
  - `isRef: boolean`
- **Return Type**: `void`
- **Calls**:
  - `describe (from vitest)`
  - `it (from vitest)`
  - `triggerCallback`
  - `triggerCallbackWithDelay`
  - `notTriggerCallbackOnChildLongPress`
  - `workOnceAndPreventModifiers`
  - `stopPropagation`
  - `stopEventListeners`
  - `triggerCallbackWithThreshold`
  - `triggerOnMouseUp`

---