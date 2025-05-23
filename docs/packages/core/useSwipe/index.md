[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useSwipe/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `Position` | `../types` |
| `computed` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useSwipe(target: MaybeRefOrGetter<EventTarget | null | undefined>, options: UseSwipeOptions): UseSwipeReturn`

<details><summary>Code</summary>

```ts
export function useSwipe(
  target: MaybeRefOrGetter<EventTarget | null | undefined>,
  options: UseSwipeOptions = {},
): UseSwipeReturn {
  const {
    threshold = 50,
    onSwipe,
    onSwipeEnd,
    onSwipeStart,
    passive = true,
  } = options

  const coordsStart = reactive<Position>({ x: 0, y: 0 })
  const coordsEnd = reactive<Position>({ x: 0, y: 0 })

  const diffX = computed(() => coordsStart.x - coordsEnd.x)
  const diffY = computed(() => coordsStart.y - coordsEnd.y)

  const { max, abs } = Math
  const isThresholdExceeded = computed(() => max(abs(diffX.value), abs(diffY.value)) >= threshold)

  const isSwiping = shallowRef(false)

  const direction = computed((): UseSwipeDirection => {
    if (!isThresholdExceeded.value)
      return 'none'

    if (abs(diffX.value) > abs(diffY.value)) {
      return diffX.value > 0
        ? 'left'
        : 'right'
    }
    else {
      return diffY.value > 0
        ? 'up'
        : 'down'
    }
  })

  const getTouchEventCoords = (e: TouchEvent) => [e.touches[0].clientX, e.touches[0].clientY]

  const updateCoordsStart = (x: number, y: number) => {
    coordsStart.x = x
    coordsStart.y = y
  }

  const updateCoordsEnd = (x: number, y: number) => {
    coordsEnd.x = x
    coordsEnd.y = y
  }

  const listenerOptions = { passive, capture: !passive }

  const onTouchEnd = (e: TouchEvent) => {
    if (isSwiping.value)
      onSwipeEnd?.(e, direction.value)

    isSwiping.value = false
  }

  const stops = [
    useEventListener(target, 'touchstart', (e: TouchEvent) => {
      if (e.touches.length !== 1)
        return
      const [x, y] = getTouchEventCoords(e)
      updateCoordsStart(x, y)
      updateCoordsEnd(x, y)
      onSwipeStart?.(e)
    }, listenerOptions),

    useEventListener(target, 'touchmove', (e: TouchEvent) => {
      if (e.touches.length !== 1)
        return
      const [x, y] = getTouchEventCoords(e)
      updateCoordsEnd(x, y)
      if (listenerOptions.capture && !listenerOptions.passive && Math.abs(diffX.value) > Math.abs(diffY.value))
        e.preventDefault()
      if (!isSwiping.value && isThresholdExceeded.value)
        isSwiping.value = true
      if (isSwiping.value)
        onSwipe?.(e)
    }, listenerOptions),

    useEventListener(target, ['touchend', 'touchcancel'], onTouchEnd, listenerOptions),
  ]

  const stop = () => stops.forEach(s => s())

  return {
    isSwiping,
    direction,
    coordsStart,
    coordsEnd,
    lengthX: diffX,
    lengthY: diffY,
    stop,

    // TODO: Remove in the next major version
    isPassiveEventSupported: true,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive swipe detection.
 *
 * @see https://vueuse.org/useSwipe
 * @param target
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeRefOrGetter<EventTarget | null | undefined>`
  - `options: UseSwipeOptions`
- **Return Type**: `UseSwipeReturn`
- **Calls**:
  - `reactive (from vue)`
  - `computed (from vue)`
  - `max`
  - `abs`
  - `shallowRef (from vue)`
  - `onSwipeEnd`
  - `useEventListener (from ../useEventListener)`
  - `getTouchEventCoords`
  - `updateCoordsStart`
  - `updateCoordsEnd`
  - `onSwipeStart`
  - `Math.abs`
  - `e.preventDefault`
  - `onSwipe`
  - `stops.forEach`
  - `s`
- **Internal Comments**:
```
// TODO: Remove in the next major version (x2)
```

### `getTouchEventCoords(e: TouchEvent): number[]`

<details><summary>Code</summary>

```ts
(e: TouchEvent) => [e.touches[0].clientX, e.touches[0].clientY]
```
</details>

- **Parameters**:
  - `e: TouchEvent`
- **Return Type**: `number[]`
### `updateCoordsStart(x: number, y: number): void`

<details><summary>Code</summary>

```ts
(x: number, y: number) => {
    coordsStart.x = x
    coordsStart.y = y
  }
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `void`
### `updateCoordsEnd(x: number, y: number): void`

<details><summary>Code</summary>

```ts
(x: number, y: number) => {
    coordsEnd.x = x
    coordsEnd.y = y
  }
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `void`
### `onTouchEnd(e: TouchEvent): void`

<details><summary>Code</summary>

```ts
(e: TouchEvent) => {
    if (isSwiping.value)
      onSwipeEnd?.(e, direction.value)

    isSwiping.value = false
  }
```
</details>

- **Parameters**:
  - `e: TouchEvent`
- **Return Type**: `void`
- **Calls**:
  - `onSwipeEnd`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => stops.forEach(s => s())
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stops.forEach`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseSwipeOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseSwipeOptions extends ConfigurableWindow {
  /**
   * Register events as passive
   *
   * @default true
   */
  passive?: boolean

  /**
   * @default 50
   */
  threshold?: number

  /**
   * Callback on swipe start
   */
  onSwipeStart?: (e: TouchEvent) => void

  /**
   * Callback on swipe moves
   */
  onSwipe?: (e: TouchEvent) => void

  /**
   * Callback on swipe ends
   */
  onSwipeEnd?: (e: TouchEvent, direction: UseSwipeDirection) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `passive` | `boolean` | ✓ |  |
| `threshold` | `number` | ✓ |  |
| `onSwipeStart` | `(e: TouchEvent) => void` | ✓ |  |
| `onSwipe` | `(e: TouchEvent) => void` | ✓ |  |
| `onSwipeEnd` | `(e: TouchEvent, direction: UseSwipeDirection) => void` | ✓ |  |

### `UseSwipeReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseSwipeReturn {
  /**
   * @deprecated No longer need this Vue 3's browser targets all supporting passive event listeners.
   *
   * This flag will always return `true` and be removed in the next major version.
   */
  isPassiveEventSupported: boolean
  isSwiping: ShallowRef<boolean>
  direction: ComputedRef<UseSwipeDirection>
  coordsStart: Readonly<Position>
  coordsEnd: Readonly<Position>
  lengthX: ComputedRef<number>
  lengthY: ComputedRef<number>
  stop: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isPassiveEventSupported` | `boolean` | ✗ |  |
| `isSwiping` | `ShallowRef<boolean>` | ✗ |  |
| `direction` | `ComputedRef<UseSwipeDirection>` | ✗ |  |
| `coordsStart` | `Readonly<Position>` | ✗ |  |
| `coordsEnd` | `Readonly<Position>` | ✗ |  |
| `lengthX` | `ComputedRef<number>` | ✗ |  |
| `lengthY` | `ComputedRef<number>` | ✗ |  |
| `stop` | `() => void` | ✗ |  |


---

## Type Aliases

### `UseSwipeDirection`

```ts
type UseSwipeDirection = 'up' | 'down' | 'left' | 'right' | 'none';
```


---