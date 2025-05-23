[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useMousePressed/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `MaybeComputedElementRef` | `../unrefElement` |
| `UseMouseSourceType` | `../useMouse` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useMousePressed(options: MousePressedOptions): { pressed: any; sourceType: any; }`

<details><summary>Code</summary>

```ts
export function useMousePressed(options: MousePressedOptions = {}) {
  const {
    touch = true,
    drag = true,
    capture = false,
    initialValue = false,
    window = defaultWindow,
  } = options

  const pressed = shallowRef(initialValue)
  const sourceType = shallowRef<UseMouseSourceType>(null)

  if (!window) {
    return {
      pressed,
      sourceType,
    }
  }

  const onPressed = (srcType: UseMouseSourceType) => (event: MouseEvent | TouchEvent | DragEvent) => {
    pressed.value = true
    sourceType.value = srcType
    options.onPressed?.(event)
  }
  const onReleased = (event: MouseEvent | TouchEvent | DragEvent) => {
    pressed.value = false
    sourceType.value = null
    options.onReleased?.(event)
  }

  const target = computed(() => unrefElement(options.target) || window)

  const listenerOptions = { passive: true, capture }
  useEventListener<MouseEvent>(target, 'mousedown', onPressed('mouse'), listenerOptions)

  useEventListener<MouseEvent>(window, 'mouseleave', onReleased, listenerOptions)
  useEventListener<MouseEvent>(window, 'mouseup', onReleased, listenerOptions)

  if (drag) {
    useEventListener<DragEvent>(target, 'dragstart', onPressed('mouse'), listenerOptions)

    useEventListener<DragEvent>(window, 'drop', onReleased, listenerOptions)
    useEventListener<DragEvent>(window, 'dragend', onReleased, listenerOptions)
  }

  if (touch) {
    useEventListener<TouchEvent>(target, 'touchstart', onPressed('touch'), listenerOptions)

    useEventListener<TouchEvent>(window, 'touchend', onReleased, listenerOptions)
    useEventListener<TouchEvent>(window, 'touchcancel', onReleased, listenerOptions)
  }

  return {
    pressed,
    sourceType,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive mouse pressing state.
 *
 * @see https://vueuse.org/useMousePressed
 * @param options
 */
```

- **Parameters**:
  - `options: MousePressedOptions`
- **Return Type**: `{ pressed: any; sourceType: any; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `options.onPressed`
  - `options.onReleased`
  - `computed (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `useEventListener (from ../useEventListener)`
  - `onPressed`
### `onPressed(srcType: UseMouseSourceType): (event: MouseEvent | DragEvent | TouchEvent) => void`

<details><summary>Code</summary>

```ts
(srcType: UseMouseSourceType) => (event: MouseEvent | TouchEvent | DragEvent) => {
    pressed.value = true
    sourceType.value = srcType
    options.onPressed?.(event)
  }
```
</details>

- **Parameters**:
  - `srcType: UseMouseSourceType`
- **Return Type**: `(event: MouseEvent | DragEvent | TouchEvent) => void`
### `onReleased(event: MouseEvent | TouchEvent | DragEvent): void`

<details><summary>Code</summary>

```ts
(event: MouseEvent | TouchEvent | DragEvent) => {
    pressed.value = false
    sourceType.value = null
    options.onReleased?.(event)
  }
```
</details>

- **Parameters**:
  - `event: MouseEvent | TouchEvent | DragEvent`
- **Return Type**: `void`
- **Calls**:
  - `options.onReleased`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `MousePressedOptions`

<details><summary>Interface Code</summary>

```ts
export interface MousePressedOptions extends ConfigurableWindow {
  /**
   * Listen to `touchstart` `touchend` events
   *
   * @default true
   */
  touch?: boolean

  /**
   * Listen to `dragstart` `drop` and `dragend` events
   *
   * @default true
   */
  drag?: boolean

  /**
   * Add event listerners with the `capture` option set to `true`
   * (see [MDN](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#capture))
   *
   * @default false
   */
  capture?: boolean

  /**
   * Initial values
   *
   * @default false
   */
  initialValue?: boolean

  /**
   * Element target to be capture the click
   */
  target?: MaybeComputedElementRef

  /**
   * Callback to be called when the mouse is pressed
   *
   * @param event
   */
  onPressed?: (event: MouseEvent | TouchEvent | DragEvent) => void

  /**
   * Callback to be called when the mouse is released
   *
   * @param event
   */
  onReleased?: (event: MouseEvent | TouchEvent | DragEvent) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `touch` | `boolean` | ✓ |  |
| `drag` | `boolean` | ✓ |  |
| `capture` | `boolean` | ✓ |  |
| `initialValue` | `boolean` | ✓ |  |
| `target` | `MaybeComputedElementRef` | ✓ |  |
| `onPressed` | `(event: MouseEvent | TouchEvent | DragEvent) => void` | ✓ |  |
| `onReleased` | `(event: MouseEvent | TouchEvent | DragEvent) => void` | ✓ |  |


---

## Type Aliases

### `UseMousePressedReturn`

```ts
type UseMousePressedReturn = ReturnType<typeof useMousePressed>;
```


---