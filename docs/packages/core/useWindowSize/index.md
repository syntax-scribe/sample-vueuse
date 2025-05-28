[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useWindowSize/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `tryOnMounted` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useMediaQuery` | `../useMediaQuery` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useWindowSize(options: UseWindowSizeOptions): { width: any; height: any; }`

<details><summary>Code</summary>

```ts
export function useWindowSize(options: UseWindowSizeOptions = {}) {
  const {
    window = defaultWindow,
    initialWidth = Number.POSITIVE_INFINITY,
    initialHeight = Number.POSITIVE_INFINITY,
    listenOrientation = true,
    includeScrollbar = true,
    type = 'inner',
  } = options

  const width = shallowRef(initialWidth)
  const height = shallowRef(initialHeight)

  const update = () => {
    if (window) {
      if (type === 'outer') {
        width.value = window.outerWidth
        height.value = window.outerHeight
      }
      else if (type === 'visual' && window.visualViewport) {
        const { width: visualViewportWidth, height: visualViewportHeight, scale } = window.visualViewport
        width.value = Math.round(visualViewportWidth * scale)
        height.value = Math.round(visualViewportHeight * scale)
      }
      else if (includeScrollbar) {
        width.value = window.innerWidth
        height.value = window.innerHeight
      }
      else {
        width.value = window.document.documentElement.clientWidth
        height.value = window.document.documentElement.clientHeight
      }
    }
  }

  update()
  tryOnMounted(update)

  const listenerOptions = { passive: true }
  useEventListener('resize', update, listenerOptions)

  if (window && type === 'visual' && window.visualViewport) {
    useEventListener(window.visualViewport, 'resize', update, listenerOptions)
  }

  if (listenOrientation) {
    const matches = useMediaQuery('(orientation: portrait)')
    watch(matches, () => update())
  }

  return { width, height }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive window size.
 *
 * @see https://vueuse.org/useWindowSize
 * @param options
 */
```

- **Parameters**:
  - `options: UseWindowSizeOptions`
- **Return Type**: `{ width: any; height: any; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `Math.round`
  - `update`
  - `tryOnMounted (from @vueuse/shared)`
  - `useEventListener (from ../useEventListener)`
  - `useMediaQuery (from ../useMediaQuery)`
  - `watch (from vue)`
### `update(): void`

<details><summary>Code</summary>

```ts
() => {
    if (window) {
      if (type === 'outer') {
        width.value = window.outerWidth
        height.value = window.outerHeight
      }
      else if (type === 'visual' && window.visualViewport) {
        const { width: visualViewportWidth, height: visualViewportHeight, scale } = window.visualViewport
        width.value = Math.round(visualViewportWidth * scale)
        height.value = Math.round(visualViewportHeight * scale)
      }
      else if (includeScrollbar) {
        width.value = window.innerWidth
        height.value = window.innerHeight
      }
      else {
        width.value = window.document.documentElement.clientWidth
        height.value = window.document.documentElement.clientHeight
      }
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `Math.round`

---

## Interfaces

### `UseWindowSizeOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseWindowSizeOptions extends ConfigurableWindow {
  initialWidth?: number
  initialHeight?: number
  /**
   * Listen to window `orientationchange` event
   *
   * @default true
   */
  listenOrientation?: boolean

  /**
   * Whether the scrollbar should be included in the width and height
   * Only effective when `type` is `'inner'`
   *
   * @default true
   */
  includeScrollbar?: boolean

  /**
   * Use `window.innerWidth` or `window.outerWidth` or `window.visualViewport`
   * visualViewport documentation from MDN(https://developer.mozilla.org/zh-CN/docs/Web/API/VisualViewport)
   * @default 'inner'
   */
  type?: 'inner' | 'outer' | 'visual'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialWidth` | `number` | ✓ |  |
| `initialHeight` | `number` | ✓ |  |
| `listenOrientation` | `boolean` | ✓ |  |
| `includeScrollbar` | `boolean` | ✓ |  |
| `type` | `'inner' | 'outer' | 'visual'` | ✓ |  |


---

## Type Aliases

### `UseWindowSizeReturn`

```ts
type UseWindowSizeReturn = ReturnType<typeof useWindowSize>;
```


---