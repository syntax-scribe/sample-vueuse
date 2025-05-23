[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 7
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useDraggable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `PointerType` | `../types` |
| `Position` | `../types` |
| `isClient` | `@vueuse/shared` |
| `toRefs` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useDraggable(target: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>, options: UseDraggableOptions): any`

<details><summary>Code</summary>

```ts
export function useDraggable(
  target: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>,
  options: UseDraggableOptions = {},
) {
  const {
    pointerTypes,
    preventDefault,
    stopPropagation,
    exact,
    onMove,
    onEnd,
    onStart,
    initialValue,
    axis = 'both',
    draggingElement = defaultWindow,
    containerElement,
    handle: draggingHandle = target,
    buttons = [0],
  } = options

  const position = deepRef<Position>(
    toValue(initialValue) ?? { x: 0, y: 0 },
  )

  const pressedDelta = deepRef<Position>()

  const filterEvent = (e: PointerEvent) => {
    if (pointerTypes)
      return pointerTypes.includes(e.pointerType as PointerType)
    return true
  }

  const handleEvent = (e: PointerEvent) => {
    if (toValue(preventDefault))
      e.preventDefault()
    if (toValue(stopPropagation))
      e.stopPropagation()
  }

  const start = (e: PointerEvent) => {
    if (!toValue(buttons).includes(e.button))
      return
    if (toValue(options.disabled) || !filterEvent(e))
      return
    if (toValue(exact) && e.target !== toValue(target))
      return

    const container = toValue(containerElement)
    const containerRect = container?.getBoundingClientRect?.()
    const targetRect = toValue(target)!.getBoundingClientRect()
    const pos = {
      x: e.clientX - (container ? targetRect.left - containerRect!.left + container.scrollLeft : targetRect.left),
      y: e.clientY - (container ? targetRect.top - containerRect!.top + container.scrollTop : targetRect.top),
    }
    if (onStart?.(pos, e) === false)
      return
    pressedDelta.value = pos
    handleEvent(e)
  }
  const move = (e: PointerEvent) => {
    if (toValue(options.disabled) || !filterEvent(e))
      return
    if (!pressedDelta.value)
      return

    const container = toValue(containerElement)
    const targetRect = toValue(target)!.getBoundingClientRect()
    let { x, y } = position.value
    if (axis === 'x' || axis === 'both') {
      x = e.clientX - pressedDelta.value.x
      if (container)
        x = Math.min(Math.max(0, x), container.scrollWidth - targetRect!.width)
    }
    if (axis === 'y' || axis === 'both') {
      y = e.clientY - pressedDelta.value.y
      if (container)
        y = Math.min(Math.max(0, y), container.scrollHeight - targetRect!.height)
    }
    position.value = {
      x,
      y,
    }
    onMove?.(position.value, e)
    handleEvent(e)
  }
  const end = (e: PointerEvent) => {
    if (toValue(options.disabled) || !filterEvent(e))
      return
    if (!pressedDelta.value)
      return
    pressedDelta.value = undefined
    onEnd?.(position.value, e)
    handleEvent(e)
  }

  if (isClient) {
    const config = () => ({
      capture: options.capture ?? true,
      passive: !toValue(preventDefault),
    })
    useEventListener(draggingHandle, 'pointerdown', start, config)
    useEventListener(draggingElement, 'pointermove', move, config)
    useEventListener(draggingElement, 'pointerup', end, config)
  }

  return {
    ...toRefs(position),
    position,
    isDragging: computed(() => !!pressedDelta.value),
    style: computed(
      () => `left:${position.value.x}px;top:${position.value.y}px;`,
    ),
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Make elements draggable.
 *
 * @see https://vueuse.org/useDraggable
 * @param target
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>`
  - `options: UseDraggableOptions`
- **Return Type**: `any`
- **Calls**:
  - `deepRef (from vue)`
  - `toValue (from vue)`
  - `pointerTypes.includes`
  - `e.preventDefault`
  - `e.stopPropagation`
  - `toValue(buttons).includes`
  - `filterEvent`
  - `container?.getBoundingClientRect`
  - `toValue(target)!.getBoundingClientRect`
  - `onStart`
  - `handleEvent`
  - `Math.min`
  - `Math.max`
  - `onMove`
  - `onEnd`
  - `useEventListener (from ../useEventListener)`
  - `toRefs (from @vueuse/shared)`
  - `computed (from vue)`
### `filterEvent(e: PointerEvent): boolean`

<details><summary>Code</summary>

```ts
(e: PointerEvent) => {
    if (pointerTypes)
      return pointerTypes.includes(e.pointerType as PointerType)
    return true
  }
```
</details>

- **Parameters**:
  - `e: PointerEvent`
- **Return Type**: `boolean`
- **Calls**:
  - `pointerTypes.includes`
### `handleEvent(e: PointerEvent): void`

<details><summary>Code</summary>

```ts
(e: PointerEvent) => {
    if (toValue(preventDefault))
      e.preventDefault()
    if (toValue(stopPropagation))
      e.stopPropagation()
  }
```
</details>

- **Parameters**:
  - `e: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `e.preventDefault`
  - `e.stopPropagation`
### `start(e: PointerEvent): void`

<details><summary>Code</summary>

```ts
(e: PointerEvent) => {
    if (!toValue(buttons).includes(e.button))
      return
    if (toValue(options.disabled) || !filterEvent(e))
      return
    if (toValue(exact) && e.target !== toValue(target))
      return

    const container = toValue(containerElement)
    const containerRect = container?.getBoundingClientRect?.()
    const targetRect = toValue(target)!.getBoundingClientRect()
    const pos = {
      x: e.clientX - (container ? targetRect.left - containerRect!.left + container.scrollLeft : targetRect.left),
      y: e.clientY - (container ? targetRect.top - containerRect!.top + container.scrollTop : targetRect.top),
    }
    if (onStart?.(pos, e) === false)
      return
    pressedDelta.value = pos
    handleEvent(e)
  }
```
</details>

- **Parameters**:
  - `e: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `toValue(buttons).includes`
  - `toValue (from vue)`
  - `filterEvent`
  - `container?.getBoundingClientRect`
  - `toValue(target)!.getBoundingClientRect`
  - `onStart`
  - `handleEvent`
### `move(e: PointerEvent): void`

<details><summary>Code</summary>

```ts
(e: PointerEvent) => {
    if (toValue(options.disabled) || !filterEvent(e))
      return
    if (!pressedDelta.value)
      return

    const container = toValue(containerElement)
    const targetRect = toValue(target)!.getBoundingClientRect()
    let { x, y } = position.value
    if (axis === 'x' || axis === 'both') {
      x = e.clientX - pressedDelta.value.x
      if (container)
        x = Math.min(Math.max(0, x), container.scrollWidth - targetRect!.width)
    }
    if (axis === 'y' || axis === 'both') {
      y = e.clientY - pressedDelta.value.y
      if (container)
        y = Math.min(Math.max(0, y), container.scrollHeight - targetRect!.height)
    }
    position.value = {
      x,
      y,
    }
    onMove?.(position.value, e)
    handleEvent(e)
  }
```
</details>

- **Parameters**:
  - `e: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `filterEvent`
  - `toValue(target)!.getBoundingClientRect`
  - `Math.min`
  - `Math.max`
  - `onMove`
  - `handleEvent`
### `end(e: PointerEvent): void`

<details><summary>Code</summary>

```ts
(e: PointerEvent) => {
    if (toValue(options.disabled) || !filterEvent(e))
      return
    if (!pressedDelta.value)
      return
    pressedDelta.value = undefined
    onEnd?.(position.value, e)
    handleEvent(e)
  }
```
</details>

- **Parameters**:
  - `e: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `filterEvent`
  - `onEnd`
  - `handleEvent`
### `config(): { capture: boolean; passive: boolean; }`

<details><summary>Code</summary>

```ts
() => ({
      capture: options.capture ?? true,
      passive: !toValue(preventDefault),
    })
```
</details>

- **Return Type**: `{ capture: boolean; passive: boolean; }`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseDraggableOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseDraggableOptions {
  /**
   * Only start the dragging when click on the element directly
   *
   * @default false
   */
  exact?: MaybeRefOrGetter<boolean>

  /**
   * Prevent events defaults
   *
   * @default false
   */
  preventDefault?: MaybeRefOrGetter<boolean>

  /**
   * Prevent events propagation
   *
   * @default false
   */
  stopPropagation?: MaybeRefOrGetter<boolean>

  /**
   * Whether dispatch events in capturing phase
   *
   * @default true
   */
  capture?: boolean

  /**
   * Element to attach `pointermove` and `pointerup` events to.
   *
   * @default window
   */
  draggingElement?: MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>

  /**
   * Element for calculating bounds (If not set, it will use the event's target).
   *
   * @default undefined
   */
  containerElement?: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>

  /**
   * Handle that triggers the drag event
   *
   * @default target
   */
  handle?: MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>

  /**
   * Pointer types that listen to.
   *
   * @default ['mouse', 'touch', 'pen']
   */
  pointerTypes?: PointerType[]

  /**
   * Initial position of the element.
   *
   * @default { x: 0, y: 0 }
   */
  initialValue?: MaybeRefOrGetter<Position>

  /**
   * Callback when the dragging starts. Return `false` to prevent dragging.
   */
  onStart?: (position: Position, event: PointerEvent) => void | false

  /**
   * Callback during dragging.
   */
  onMove?: (position: Position, event: PointerEvent) => void

  /**
   * Callback when dragging end.
   */
  onEnd?: (position: Position, event: PointerEvent) => void

  /**
   * Axis to drag on.
   *
   * @default 'both'
   */
  axis?: 'x' | 'y' | 'both'

  /**
   * Disabled drag and drop.
   *
   * @default false
   */
  disabled?: MaybeRefOrGetter<boolean>

  /**
   * Mouse buttons that are allowed to trigger drag events.
   *
   * - `0`: Main button, usually the left button or the un-initialized state
   * - `1`: Auxiliary button, usually the wheel button or the middle button (if present)
   * - `2`: Secondary button, usually the right button
   * - `3`: Fourth button, typically the Browser Back button
   * - `4`: Fifth button, typically the Browser Forward button
   *
   * @see https://developer.mozilla.org/en-US/docs/Web/API/MouseEvent/button#value
   * @default [0]
   */
  buttons?: MaybeRefOrGetter<number[]>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `exact` | `MaybeRefOrGetter<boolean>` | ✓ |  |
| `preventDefault` | `MaybeRefOrGetter<boolean>` | ✓ |  |
| `stopPropagation` | `MaybeRefOrGetter<boolean>` | ✓ |  |
| `capture` | `boolean` | ✓ |  |
| `draggingElement` | `MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>` | ✓ |  |
| `containerElement` | `MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>` | ✓ |  |
| `handle` | `MaybeRefOrGetter<HTMLElement | SVGElement | null | undefined>` | ✓ |  |
| `pointerTypes` | `PointerType[]` | ✓ |  |
| `initialValue` | `MaybeRefOrGetter<Position>` | ✓ |  |
| `onStart` | `(position: Position, event: PointerEvent) => void | false` | ✓ |  |
| `onMove` | `(position: Position, event: PointerEvent) => void` | ✓ |  |
| `onEnd` | `(position: Position, event: PointerEvent) => void` | ✓ |  |
| `axis` | `'x' | 'y' | 'both'` | ✓ |  |
| `disabled` | `MaybeRefOrGetter<boolean>` | ✓ |  |
| `buttons` | `MaybeRefOrGetter<number[]>` | ✓ |  |


---

## Type Aliases

### `UseDraggableReturn`

```ts
type UseDraggableReturn = ReturnType<typeof useDraggable>;
```


---