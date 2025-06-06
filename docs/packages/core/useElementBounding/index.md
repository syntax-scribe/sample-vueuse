[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 8 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useElementBounding/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeComputedElementRef` | `../unrefElement` |
| `tryOnMounted` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |
| `useMutationObserver` | `../useMutationObserver` |
| `useResizeObserver` | `../useResizeObserver` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useElementBounding(target: MaybeComputedElementRef, options: UseElementBoundingOptions): { height: any; bottom: any; left: any; right: any; top: any; width: any; x: any; y: any; update: () => void; }`

<details><summary>Code</summary>

```ts
export function useElementBounding(
  target: MaybeComputedElementRef,
  options: UseElementBoundingOptions = {},
) {
  const {
    reset = true,
    windowResize = true,
    windowScroll = true,
    immediate = true,
    updateTiming = 'sync',
  } = options

  const height = shallowRef(0)
  const bottom = shallowRef(0)
  const left = shallowRef(0)
  const right = shallowRef(0)
  const top = shallowRef(0)
  const width = shallowRef(0)
  const x = shallowRef(0)
  const y = shallowRef(0)

  function recalculate() {
    const el = unrefElement(target)

    if (!el) {
      if (reset) {
        height.value = 0
        bottom.value = 0
        left.value = 0
        right.value = 0
        top.value = 0
        width.value = 0
        x.value = 0
        y.value = 0
      }
      return
    }

    const rect = el.getBoundingClientRect()

    height.value = rect.height
    bottom.value = rect.bottom
    left.value = rect.left
    right.value = rect.right
    top.value = rect.top
    width.value = rect.width
    x.value = rect.x
    y.value = rect.y
  }

  function update() {
    if (updateTiming === 'sync')
      recalculate()
    else if (updateTiming === 'next-frame')
      requestAnimationFrame(() => recalculate())
  }

  useResizeObserver(target, update)
  watch(() => unrefElement(target), ele => !ele && update())
  // trigger by css or style
  useMutationObserver(target, update, {
    attributeFilter: ['style', 'class'],
  })

  if (windowScroll)
    useEventListener('scroll', update, { capture: true, passive: true })
  if (windowResize)
    useEventListener('resize', update, { passive: true })

  tryOnMounted(() => {
    if (immediate)
      update()
  })

  return {
    height,
    bottom,
    left,
    right,
    top,
    width,
    x,
    y,
    update,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive bounding box of an HTML element.
 *
 * @see https://vueuse.org/useElementBounding
 * @param target
 */
```

- **Parameters**:
  - `target: MaybeComputedElementRef`
  - `options: UseElementBoundingOptions`
- **Return Type**: `{ height: any; bottom: any; left: any; right: any; top: any; width: any; x: any; y: any; update: () => void; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `el.getBoundingClientRect`
  - `recalculate`
  - `requestAnimationFrame`
  - `useResizeObserver (from ../useResizeObserver)`
  - `watch (from vue)`
  - `update`
  - `useMutationObserver (from ../useMutationObserver)`
  - `useEventListener (from ../useEventListener)`
  - `tryOnMounted (from @vueuse/shared)`
- **Internal Comments**:
```
// trigger by css or style (x3)
```

### `recalculate(): void`

<details><summary>Code</summary>

```ts
function recalculate() {
    const el = unrefElement(target)

    if (!el) {
      if (reset) {
        height.value = 0
        bottom.value = 0
        left.value = 0
        right.value = 0
        top.value = 0
        width.value = 0
        x.value = 0
        y.value = 0
      }
      return
    }

    const rect = el.getBoundingClientRect()

    height.value = rect.height
    bottom.value = rect.bottom
    left.value = rect.left
    right.value = rect.right
    top.value = rect.top
    width.value = rect.width
    x.value = rect.x
    y.value = rect.y
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `unrefElement (from ../unrefElement)`
  - `el.getBoundingClientRect`
### `update(): void`

<details><summary>Code</summary>

```ts
function update() {
    if (updateTiming === 'sync')
      recalculate()
    else if (updateTiming === 'next-frame')
      requestAnimationFrame(() => recalculate())
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `recalculate`
  - `requestAnimationFrame`

---

## Interfaces

### `UseElementBoundingOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseElementBoundingOptions {
  /**
   * Reset values to 0 on component unmounted
   *
   * @default true
   */
  reset?: boolean

  /**
   * Listen to window resize event
   *
   * @default true
   */
  windowResize?: boolean
  /**
   * Listen to window scroll event
   *
   * @default true
   */
  windowScroll?: boolean

  /**
   * Immediately call update on component mounted
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Timing to recalculate the bounding box
   *
   * Setting to `next-frame` can be useful when using this together with something like {@link useBreakpoints}
   * and therefore the layout (which influences the bounding box of the observed element) is not updated on the current tick.
   *
   * @default 'sync'
   */
  updateTiming?: 'sync' | 'next-frame'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `reset` | `boolean` | ✓ |  |
| `windowResize` | `boolean` | ✓ |  |
| `windowScroll` | `boolean` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `updateTiming` | `'sync' | 'next-frame'` | ✓ |  |


---

## Type Aliases

### `UseElementBoundingReturn`

```ts
type UseElementBoundingReturn = ReturnType<typeof useElementBounding>;
```


---