[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 2 |
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
📂 **`packages/core/useElementSize/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeComputedElementRef` | `../unrefElement` |
| `UseResizeObserverOptions` | `../useResizeObserver` |
| `toArray` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useResizeObserver` | `../useResizeObserver` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `boxSize` | `readonly ResizeObserverSize[]` | const | `box === 'border-box'
        ? entry.borderBoxSize
        : box === 'content-box'
          ? entry.contentBoxSize
          : entry.devicePixelContentBoxSize` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `useElementSize(target: MaybeComputedElementRef, initialSize: ElementSize, options: UseResizeObserverOptions): { width: any; height: any; stop: () => void; }`

<details><summary>Code</summary>

```ts
export function useElementSize(
  target: MaybeComputedElementRef,
  initialSize: ElementSize = { width: 0, height: 0 },
  options: UseResizeObserverOptions = {},
) {
  const { window = defaultWindow, box = 'content-box' } = options
  const isSVG = computed(() => unrefElement(target)?.namespaceURI?.includes('svg'))
  const width = shallowRef(initialSize.width)
  const height = shallowRef(initialSize.height)

  const { stop: stop1 } = useResizeObserver(
    target,
    ([entry]) => {
      const boxSize = box === 'border-box'
        ? entry.borderBoxSize
        : box === 'content-box'
          ? entry.contentBoxSize
          : entry.devicePixelContentBoxSize

      if (window && isSVG.value) {
        const $elem = unrefElement(target)
        if ($elem) {
          const rect = $elem.getBoundingClientRect()
          width.value = rect.width
          height.value = rect.height
        }
      }
      else {
        if (boxSize) {
          const formatBoxSize = toArray(boxSize)
          width.value = formatBoxSize.reduce((acc, { inlineSize }) => acc + inlineSize, 0)
          height.value = formatBoxSize.reduce((acc, { blockSize }) => acc + blockSize, 0)
        }
        else {
          // fallback
          width.value = entry.contentRect.width
          height.value = entry.contentRect.height
        }
      }
    },
    options,
  )

  tryOnMounted(() => {
    const ele = unrefElement(target)
    if (ele) {
      width.value = 'offsetWidth' in ele ? ele.offsetWidth : initialSize.width
      height.value = 'offsetHeight' in ele ? ele.offsetHeight : initialSize.height
    }
  })

  const stop2 = watch(
    () => unrefElement(target),
    (ele) => {
      width.value = ele ? initialSize.width : 0
      height.value = ele ? initialSize.height : 0
    },
  )

  function stop() {
    stop1()
    stop2()
  }

  return {
    width,
    height,
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive size of an HTML element.
 *
 * @see https://vueuse.org/useElementSize
 */
```

- **Parameters**:
  - `target: MaybeComputedElementRef`
  - `initialSize: ElementSize`
  - `options: UseResizeObserverOptions`
- **Return Type**: `{ width: any; height: any; stop: () => void; }`
- **Calls**:
  - `computed (from vue)`
  - `unrefElement(target)?.namespaceURI?.includes`
  - `shallowRef (from vue)`
  - `useResizeObserver (from ../useResizeObserver)`
  - `unrefElement (from ../unrefElement)`
  - `$elem.getBoundingClientRect`
  - `toArray (from @vueuse/shared)`
  - `formatBoxSize.reduce`
  - `tryOnMounted (from @vueuse/shared)`
  - `watch (from vue)`
  - `stop1`
  - `stop2`
- **Internal Comments**:
```
// fallback (x4)
```

### `stop(): void`

<details><summary>Code</summary>

```ts
function stop() {
    stop1()
    stop2()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stop1`
  - `stop2`

---

## Interfaces

### `ElementSize`

<details><summary>Interface Code</summary>

```ts
export interface ElementSize {
  width: number
  height: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `width` | `number` | ✗ |  |
| `height` | `number` | ✗ |  |


---

## Type Aliases

### `UseElementSizeReturn`

```ts
type UseElementSizeReturn = ReturnType<typeof useElementSize>;
```


---