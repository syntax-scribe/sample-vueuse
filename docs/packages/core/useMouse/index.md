[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 21 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 9 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 4 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useMouse/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableEventFilter` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `Position` | `../types` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `UseMouseBuiltinExtractors` | `Record<UseMouseCoordType, UseMouseEventExtractor>` | const | `{
  page: event => [event.pageX, event.pageY],
  client: event => [event.clientX, event.clientY],
  screen: event => [event.screenX, event.screenY],
  movement: event => (event instanceof MouseEvent
    ? [event.movementX, event.movementY]
    : null
  ),
} as const` | ✗ |
| `_prevMouseEvent` | `MouseEvent | null` | let/var | `null` | ✗ |
| `_prevScrollX` | `number` | let/var | `0` | ✗ |
| `_prevScrollY` | `number` | let/var | `0` | ✗ |
| `extractor` | `UseMouseEventExtractor` | const | `typeof type === 'function'
    ? type
    : UseMouseBuiltinExtractors[type]` | ✗ |
| `mouseHandlerWrapper` | `(event: MouseEvent) => any` | const | `eventFilter
    ? (event: MouseEvent) => eventFilter(() => mouseHandler(event), {} as any)
    : (event: MouseEvent) => mouseHandler(event)` | ✗ |
| `touchHandlerWrapper` | `(event: TouchEvent) => any` | const | `eventFilter
    ? (event: TouchEvent) => eventFilter(() => touchHandler(event), {} as any)
    : (event: TouchEvent) => touchHandler(event)` | ✗ |
| `scrollHandlerWrapper` | `() => any` | const | `eventFilter
    ? () => eventFilter(() => scrollHandler(), {} as any)
    : () => scrollHandler()` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Functions

### `page(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.pageX, event.pageY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `client(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.clientX, event.clientY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `screen(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.screenX, event.screenY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `movement(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => (event instanceof MouseEvent
    ? [event.movementX, event.movementY]
    : null
  )
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `page(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.pageX, event.pageY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `client(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.clientX, event.clientY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `screen(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.screenX, event.screenY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `movement(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => (event instanceof MouseEvent
    ? [event.movementX, event.movementY]
    : null
  )
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `page(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.pageX, event.pageY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `client(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.clientX, event.clientY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `screen(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.screenX, event.screenY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `movement(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => (event instanceof MouseEvent
    ? [event.movementX, event.movementY]
    : null
  )
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `page(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.pageX, event.pageY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `client(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.clientX, event.clientY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `screen(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => [event.screenX, event.screenY]
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `movement(event: MouseEvent | Touch): [number, number]`

<details><summary>Code</summary>

```ts
event => (event instanceof MouseEvent
    ? [event.movementX, event.movementY]
    : null
  )
```
</details>

- **Parameters**:
  - `event: MouseEvent | Touch`
- **Return Type**: `[number, number]`
### `useMouse(options: UseMouseOptions): { x: any; y: any; sourceType: any; }`

<details><summary>Code</summary>

```ts
export function useMouse(options: UseMouseOptions = {}) {
  const {
    type = 'page',
    touch = true,
    resetOnTouchEnds = false,
    initialValue = { x: 0, y: 0 },
    window = defaultWindow,
    target = window,
    scroll = true,
    eventFilter,
  } = options

  let _prevMouseEvent: MouseEvent | null = null
  let _prevScrollX = 0
  let _prevScrollY = 0

  const x = shallowRef(initialValue.x)
  const y = shallowRef(initialValue.y)
  const sourceType = shallowRef<UseMouseSourceType>(null)

  const extractor = typeof type === 'function'
    ? type
    : UseMouseBuiltinExtractors[type]

  const mouseHandler = (event: MouseEvent) => {
    const result = extractor(event)
    _prevMouseEvent = event

    if (result) {
      [x.value, y.value] = result
      sourceType.value = 'mouse'
    }

    if (window) {
      _prevScrollX = window.scrollX
      _prevScrollY = window.scrollY
    }
  }

  const touchHandler = (event: TouchEvent) => {
    if (event.touches.length > 0) {
      const result = extractor(event.touches[0])
      if (result) {
        [x.value, y.value] = result
        sourceType.value = 'touch'
      }
    }
  }

  const scrollHandler = () => {
    if (!_prevMouseEvent || !window)
      return
    const pos = extractor(_prevMouseEvent)

    if (_prevMouseEvent instanceof MouseEvent && pos) {
      x.value = pos[0] + window.scrollX - _prevScrollX
      y.value = pos[1] + window.scrollY - _prevScrollY
    }
  }

  const reset = () => {
    x.value = initialValue.x
    y.value = initialValue.y
  }

  const mouseHandlerWrapper = eventFilter
    ? (event: MouseEvent) => eventFilter(() => mouseHandler(event), {} as any)
    : (event: MouseEvent) => mouseHandler(event)

  const touchHandlerWrapper = eventFilter
    ? (event: TouchEvent) => eventFilter(() => touchHandler(event), {} as any)
    : (event: TouchEvent) => touchHandler(event)

  const scrollHandlerWrapper = eventFilter
    ? () => eventFilter(() => scrollHandler(), {} as any)
    : () => scrollHandler()

  if (target) {
    const listenerOptions = { passive: true }
    useEventListener(target, ['mousemove', 'dragover'], mouseHandlerWrapper, listenerOptions)
    if (touch && type !== 'movement') {
      useEventListener(target, ['touchstart', 'touchmove'], touchHandlerWrapper, listenerOptions)
      if (resetOnTouchEnds)
        useEventListener(target, 'touchend', reset, listenerOptions)
    }
    if (scroll && type === 'page')
      useEventListener(window, 'scroll', scrollHandlerWrapper, listenerOptions)
  }

  return {
    x,
    y,
    sourceType,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive mouse position.
 *
 * @see https://vueuse.org/useMouse
 * @param options
 */
```

- **Parameters**:
  - `options: UseMouseOptions`
- **Return Type**: `{ x: any; y: any; sourceType: any; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `extractor`
  - `eventFilter`
  - `mouseHandler`
  - `touchHandler`
  - `scrollHandler`
  - `useEventListener (from ../useEventListener)`
### `mouseHandler(event: MouseEvent): void`

<details><summary>Code</summary>

```ts
(event: MouseEvent) => {
    const result = extractor(event)
    _prevMouseEvent = event

    if (result) {
      [x.value, y.value] = result
      sourceType.value = 'mouse'
    }

    if (window) {
      _prevScrollX = window.scrollX
      _prevScrollY = window.scrollY
    }
  }
```
</details>

- **Parameters**:
  - `event: MouseEvent`
- **Return Type**: `void`
- **Calls**:
  - `extractor`
### `touchHandler(event: TouchEvent): void`

<details><summary>Code</summary>

```ts
(event: TouchEvent) => {
    if (event.touches.length > 0) {
      const result = extractor(event.touches[0])
      if (result) {
        [x.value, y.value] = result
        sourceType.value = 'touch'
      }
    }
  }
```
</details>

- **Parameters**:
  - `event: TouchEvent`
- **Return Type**: `void`
- **Calls**:
  - `extractor`
### `scrollHandler(): void`

<details><summary>Code</summary>

```ts
() => {
    if (!_prevMouseEvent || !window)
      return
    const pos = extractor(_prevMouseEvent)

    if (_prevMouseEvent instanceof MouseEvent && pos) {
      x.value = pos[0] + window.scrollX - _prevScrollX
      y.value = pos[1] + window.scrollY - _prevScrollY
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `extractor`
### `reset(): void`

<details><summary>Code</summary>

```ts
() => {
    x.value = initialValue.x
    y.value = initialValue.y
  }
```
</details>

- **Return Type**: `void`

---

## Interfaces

### `UseMouseOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseMouseOptions extends ConfigurableWindow, ConfigurableEventFilter {
  /**
   * Mouse position based by page, client, screen, or relative to previous position
   *
   * @default 'page'
   */
  type?: UseMouseCoordType | UseMouseEventExtractor

  /**
   * Listen events on `target` element
   *
   * @default 'Window'
   */
  target?: MaybeRefOrGetter<Window | EventTarget | null | undefined>

  /**
   * Listen to `touchmove` events
   *
   * @default true
   */
  touch?: boolean

  /**
   * Listen to `scroll` events on window, only effective on type `page`
   *
   * @default true
   */
  scroll?: boolean

  /**
   * Reset to initial value when `touchend` event fired
   *
   * @default false
   */
  resetOnTouchEnds?: boolean

  /**
   * Initial values
   */
  initialValue?: Position
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `type` | `UseMouseCoordType | UseMouseEventExtractor` | ✓ |  |
| `target` | `MaybeRefOrGetter<Window | EventTarget | null | undefined>` | ✓ |  |
| `touch` | `boolean` | ✓ |  |
| `scroll` | `boolean` | ✓ |  |
| `resetOnTouchEnds` | `boolean` | ✓ |  |
| `initialValue` | `Position` | ✓ |  |


---

## Type Aliases

### `UseMouseCoordType`

```ts
type UseMouseCoordType = 'page' | 'client' | 'screen' | 'movement';
```

### `UseMouseSourceType`

```ts
type UseMouseSourceType = 'mouse' | 'touch' | null;
```

### `UseMouseEventExtractor`

```ts
type UseMouseEventExtractor = (event: MouseEvent | Touch) => [x: number, y: number] | null | undefined;
```

### `UseMouseReturn`

```ts
type UseMouseReturn = ReturnType<typeof useMouse>;
```


---