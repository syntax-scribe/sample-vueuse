[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 13 |
| 📊 Variables & Constants | 11 |
| 🟢 Vue Composition API | 4 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useScroll/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `noop` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `useDebounceFn` | `@vueuse/shared` |
| `useThrottleFn` | `@vueuse/shared` |
| `computed` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `ARRIVED_STATE_THRESHOLD_PIXELS` | `1` | const | `1` | ✗ |
| `scrollContainer` | `Element` | const | `(_element as Window)?.document?.documentElement
        || (_element as Document)?.documentElement
        || (_element as Element)` | ✗ |
| `el` | `Element` | const | `(
      (target as Window)?.document?.documentElement
      || (target as Document)?.documentElement
      || unrefElement(target as HTMLElement | SVGElement)
    ) as Element` | ✗ |
| `directionMultipler` | `1 | -1` | const | `direction === 'rtl' ? -1 : 1` | ✗ |
| `scrollLeft` | `number` | const | `el.scrollLeft` | ✗ |
| `left` | `boolean` | const | `Math.abs(scrollLeft * directionMultipler) <= (offset.left || 0)` | ✗ |
| `right` | `boolean` | const | `Math.abs(scrollLeft * directionMultipler)
      + el.clientWidth >= el.scrollWidth
      - (offset.right || 0)
      - ARRIVED_STATE_THRESHOLD_PIXELS` | ✗ |
| `scrollTop` | `number` | let/var | `el.scrollTop` | ✗ |
| `top` | `boolean` | const | `Math.abs(scrollTop) <= (offset.top || 0)` | ✗ |
| `bottom` | `boolean` | const | `Math.abs(scrollTop)
      + el.clientHeight >= el.scrollHeight
      - (offset.bottom || 0)
      - ARRIVED_STATE_THRESHOLD_PIXELS` | ✗ |
| `eventTarget` | `HTMLElement` | const | `(
      (e.target as Document).documentElement ?? e.target
    ) as HTMLElement` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


---

## Functions

### `useScroll(element: MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>, options: UseScrollOptions): { x: any; y: any; isScrolling: any; arrivedState: any; directions: any; measure(): void; }`

<details><summary>Code</summary>

```ts
export function useScroll(
  element: MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>,
  options: UseScrollOptions = {},
) {
  const {
    throttle = 0,
    idle = 200,
    onStop = noop,
    onScroll = noop,
    offset = {
      left: 0,
      right: 0,
      top: 0,
      bottom: 0,
    },
    eventListenerOptions = {
      capture: false,
      passive: true,
    },
    behavior = 'auto',
    window = defaultWindow,
    onError = (e) => { console.error(e) },
  } = options

  const internalX = shallowRef(0)
  const internalY = shallowRef(0)

  // Use a computed for x and y because we want to write the value to the refs
  // during a `scrollTo()` without firing additional `scrollTo()`s in the process.
  const x = computed({
    get() {
      return internalX.value
    },
    set(x) {
      scrollTo(x, undefined)
    },
  })

  const y = computed({
    get() {
      return internalY.value
    },
    set(y) {
      scrollTo(undefined, y)
    },
  })

  function scrollTo(_x: number | undefined, _y: number | undefined) {
    if (!window)
      return

    const _element = toValue(element)
    if (!_element)
      return

    (_element instanceof Document ? window.document.body : _element)?.scrollTo({
      top: toValue(_y) ?? y.value,
      left: toValue(_x) ?? x.value,
      behavior: toValue(behavior),
    })
    const scrollContainer
      = (_element as Window)?.document?.documentElement
        || (_element as Document)?.documentElement
        || (_element as Element)
    if (x != null)
      internalX.value = scrollContainer.scrollLeft
    if (y != null)
      internalY.value = scrollContainer.scrollTop
  }

  const isScrolling = shallowRef(false)
  const arrivedState = reactive({
    left: true,
    right: false,
    top: true,
    bottom: false,
  })
  const directions = reactive({
    left: false,
    right: false,
    top: false,
    bottom: false,
  })

  const onScrollEnd = (e: Event) => {
    // dedupe if support native scrollend event
    if (!isScrolling.value)
      return

    isScrolling.value = false
    directions.left = false
    directions.right = false
    directions.top = false
    directions.bottom = false
    onStop(e)
  }
  const onScrollEndDebounced = useDebounceFn(onScrollEnd, throttle + idle)

  const setArrivedState = (target: HTMLElement | SVGElement | Window | Document | null | undefined) => {
    if (!window)
      return

    const el: Element = (
      (target as Window)?.document?.documentElement
      || (target as Document)?.documentElement
      || unrefElement(target as HTMLElement | SVGElement)
    ) as Element

    const { display, flexDirection, direction } = getComputedStyle(el)
    const directionMultipler = direction === 'rtl' ? -1 : 1

    const scrollLeft = el.scrollLeft
    directions.left = scrollLeft < internalX.value
    directions.right = scrollLeft > internalX.value

    const left = Math.abs(scrollLeft * directionMultipler) <= (offset.left || 0)
    const right = Math.abs(scrollLeft * directionMultipler)
      + el.clientWidth >= el.scrollWidth
      - (offset.right || 0)
      - ARRIVED_STATE_THRESHOLD_PIXELS

    if (display === 'flex' && flexDirection === 'row-reverse') {
      arrivedState.left = right
      arrivedState.right = left
    }
    else {
      arrivedState.left = left
      arrivedState.right = right
    }

    internalX.value = scrollLeft

    let scrollTop = el.scrollTop

    // patch for mobile compatible
    if (target === window.document && !scrollTop)
      scrollTop = window.document.body.scrollTop

    directions.top = scrollTop < internalY.value
    directions.bottom = scrollTop > internalY.value
    const top = Math.abs(scrollTop) <= (offset.top || 0)
    const bottom = Math.abs(scrollTop)
      + el.clientHeight >= el.scrollHeight
      - (offset.bottom || 0)
      - ARRIVED_STATE_THRESHOLD_PIXELS

    /**
     * reverse columns and rows behave exactly the other way around,
     * bottom is treated as top and top is treated as the negative version of bottom
     */
    if (display === 'flex' && flexDirection === 'column-reverse') {
      arrivedState.top = bottom
      arrivedState.bottom = top
    }
    else {
      arrivedState.top = top
      arrivedState.bottom = bottom
    }

    internalY.value = scrollTop
  }

  const onScrollHandler = (e: Event) => {
    if (!window)
      return

    const eventTarget = (
      (e.target as Document).documentElement ?? e.target
    ) as HTMLElement

    setArrivedState(eventTarget)

    isScrolling.value = true
    onScrollEndDebounced(e)
    onScroll(e)
  }

  useEventListener(
    element,
    'scroll',
    throttle ? useThrottleFn(onScrollHandler, throttle, true, false) : onScrollHandler,
    eventListenerOptions,
  )

  tryOnMounted(() => {
    try {
      const _element = toValue(element)
      if (!_element)
        return
      setArrivedState(_element)
    }
    catch (e) {
      onError(e)
    }
  })

  useEventListener(
    element,
    'scrollend',
    onScrollEnd,
    eventListenerOptions,
  )

  return {
    x,
    y,
    isScrolling,
    arrivedState,
    directions,
    measure() {
      const _element = toValue(element)

      if (window && _element)
        setArrivedState(_element)
    },
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive scroll.
 *
 * @see https://vueuse.org/useScroll
 * @param element
 * @param options
 */
```

- **Parameters**:
  - `element: MaybeRefOrGetter<HTMLElement | SVGElement | Window | Document | null | undefined>`
  - `options: UseScrollOptions`
- **Return Type**: `{ x: any; y: any; isScrolling: any; arrivedState: any; directions: any; measure(): void; }`
- **Calls**:
  - `console.error`
  - `shallowRef (from vue)`
  - `computed (from vue)`
  - `scrollTo`
  - `toValue (from vue)`
  - `(_element instanceof Document ? window.document.body : _element)?.scrollTo`
  - `reactive (from vue)`
  - `onStop`
  - `useDebounceFn (from @vueuse/shared)`
  - `unrefElement (from ../unrefElement)`
  - `getComputedStyle`
  - `Math.abs`
  - `setArrivedState`
  - `onScrollEndDebounced`
  - `onScroll`
  - `useEventListener (from ../useEventListener)`
  - `useThrottleFn (from @vueuse/shared)`
  - `tryOnMounted (from @vueuse/shared)`
  - `onError`
- **Internal Comments**:
```
// Use a computed for x and y because we want to write the value to the refs (x2)
// during a `scrollTo()` without firing additional `scrollTo()`s in the process. (x2)
// dedupe if support native scrollend event
// patch for mobile compatible
/**
     * reverse columns and rows behave exactly the other way around,
     * bottom is treated as top and top is treated as the negative version of bottom
     */
```

### `scrollTo(_x: number | undefined, _y: number | undefined): void`

<details><summary>Code</summary>

```ts
function scrollTo(_x: number | undefined, _y: number | undefined) {
    if (!window)
      return

    const _element = toValue(element)
    if (!_element)
      return

    (_element instanceof Document ? window.document.body : _element)?.scrollTo({
      top: toValue(_y) ?? y.value,
      left: toValue(_x) ?? x.value,
      behavior: toValue(behavior),
    })
    const scrollContainer
      = (_element as Window)?.document?.documentElement
        || (_element as Document)?.documentElement
        || (_element as Element)
    if (x != null)
      internalX.value = scrollContainer.scrollLeft
    if (y != null)
      internalY.value = scrollContainer.scrollTop
  }
```
</details>

- **Parameters**:
  - `_x: number | undefined`
  - `_y: number | undefined`
- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `(_element instanceof Document ? window.document.body : _element)?.scrollTo`
### `onScrollEnd(e: Event): void`

<details><summary>Code</summary>

```ts
(e: Event) => {
    // dedupe if support native scrollend event
    if (!isScrolling.value)
      return

    isScrolling.value = false
    directions.left = false
    directions.right = false
    directions.top = false
    directions.bottom = false
    onStop(e)
  }
```
</details>

- **Parameters**:
  - `e: Event`
- **Return Type**: `void`
- **Calls**:
  - `onStop`
- **Internal Comments**:
```
// dedupe if support native scrollend event
```

### `setArrivedState(target: HTMLElement | SVGElement | Window | Document | null | undefined): void`

<details><summary>Code</summary>

```ts
(target: HTMLElement | SVGElement | Window | Document | null | undefined) => {
    if (!window)
      return

    const el: Element = (
      (target as Window)?.document?.documentElement
      || (target as Document)?.documentElement
      || unrefElement(target as HTMLElement | SVGElement)
    ) as Element

    const { display, flexDirection, direction } = getComputedStyle(el)
    const directionMultipler = direction === 'rtl' ? -1 : 1

    const scrollLeft = el.scrollLeft
    directions.left = scrollLeft < internalX.value
    directions.right = scrollLeft > internalX.value

    const left = Math.abs(scrollLeft * directionMultipler) <= (offset.left || 0)
    const right = Math.abs(scrollLeft * directionMultipler)
      + el.clientWidth >= el.scrollWidth
      - (offset.right || 0)
      - ARRIVED_STATE_THRESHOLD_PIXELS

    if (display === 'flex' && flexDirection === 'row-reverse') {
      arrivedState.left = right
      arrivedState.right = left
    }
    else {
      arrivedState.left = left
      arrivedState.right = right
    }

    internalX.value = scrollLeft

    let scrollTop = el.scrollTop

    // patch for mobile compatible
    if (target === window.document && !scrollTop)
      scrollTop = window.document.body.scrollTop

    directions.top = scrollTop < internalY.value
    directions.bottom = scrollTop > internalY.value
    const top = Math.abs(scrollTop) <= (offset.top || 0)
    const bottom = Math.abs(scrollTop)
      + el.clientHeight >= el.scrollHeight
      - (offset.bottom || 0)
      - ARRIVED_STATE_THRESHOLD_PIXELS

    /**
     * reverse columns and rows behave exactly the other way around,
     * bottom is treated as top and top is treated as the negative version of bottom
     */
    if (display === 'flex' && flexDirection === 'column-reverse') {
      arrivedState.top = bottom
      arrivedState.bottom = top
    }
    else {
      arrivedState.top = top
      arrivedState.bottom = bottom
    }

    internalY.value = scrollTop
  }
```
</details>

- **Parameters**:
  - `target: HTMLElement | SVGElement | Window | Document | null | undefined`
- **Return Type**: `void`
- **Calls**:
  - `unrefElement (from ../unrefElement)`
  - `getComputedStyle`
  - `Math.abs`
- **Internal Comments**:
```
// patch for mobile compatible
/**
     * reverse columns and rows behave exactly the other way around,
     * bottom is treated as top and top is treated as the negative version of bottom
     */
```

### `onScrollHandler(e: Event): void`

<details><summary>Code</summary>

```ts
(e: Event) => {
    if (!window)
      return

    const eventTarget = (
      (e.target as Document).documentElement ?? e.target
    ) as HTMLElement

    setArrivedState(eventTarget)

    isScrolling.value = true
    onScrollEndDebounced(e)
    onScroll(e)
  }
```
</details>

- **Parameters**:
  - `e: Event`
- **Return Type**: `void`
- **Calls**:
  - `setArrivedState`
  - `onScrollEndDebounced`
  - `onScroll`

---

## Interfaces

### `UseScrollOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseScrollOptions extends ConfigurableWindow {
  /**
   * Throttle time for scroll event, it’s disabled by default.
   *
   * @default 0
   */
  throttle?: number

  /**
   * The check time when scrolling ends.
   * This configuration will be setting to (throttle + idle) when the `throttle` is configured.
   *
   * @default 200
   */
  idle?: number

  /**
   * Offset arrived states by x pixels
   *
   */
  offset?: {
    left?: number
    right?: number
    top?: number
    bottom?: number
  }

  /**
   * Trigger it when scrolling.
   *
   */
  onScroll?: (e: Event) => void

  /**
   * Trigger it when scrolling ends.
   *
   */
  onStop?: (e: Event) => void

  /**
   * Listener options for scroll event.
   *
   * @default {capture: false, passive: true}
   */
  eventListenerOptions?: boolean | AddEventListenerOptions

  /**
   * Optionally specify a scroll behavior of `auto` (default, not smooth scrolling) or
   * `smooth` (for smooth scrolling) which takes effect when changing the `x` or `y` refs.
   *
   * @default 'auto'
   */
  behavior?: MaybeRefOrGetter<ScrollBehavior>

  /**
   * On error callback
   *
   * Default log error to `console.error`
   */
  onError?: (error: unknown) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `throttle` | `number` | ✓ |  |
| `idle` | `number` | ✓ |  |
| `offset` | `{
    left?: number
    right?: number
    top?: number
    bottom?: number
  }` | ✓ |  |
| `onScroll` | `(e: Event) => void` | ✓ |  |
| `onStop` | `(e: Event) => void` | ✓ |  |
| `eventListenerOptions` | `boolean | AddEventListenerOptions` | ✓ |  |
| `behavior` | `MaybeRefOrGetter<ScrollBehavior>` | ✓ |  |
| `onError` | `(error: unknown) => void` | ✓ |  |


---

## Type Aliases

### `UseScrollReturn`

```ts
type UseScrollReturn = ReturnType<typeof useScroll>;
```


---