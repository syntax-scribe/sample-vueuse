[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 1 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useImage/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `UseAsyncStateOptions` | `../useAsyncState` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `useAsyncState` | `../useAsyncState` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `img` | `HTMLImageElement` | const | `new Image()` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `loadImage` | *none* | new Promise(...) |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `loadImage(options: UseImageOptions): Promise<HTMLImageElement>`

<details><summary>Code</summary>

```ts
async function loadImage(options: UseImageOptions): Promise<HTMLImageElement> {
  return new Promise((resolve, reject) => {
    const img = new Image()
    const { src, srcset, sizes, class: clazz, loading, crossorigin, referrerPolicy, width, height, decoding, fetchPriority, ismap, usemap } = options

    img.src = src

    if (srcset != null)
      img.srcset = srcset
    if (sizes != null)
      img.sizes = sizes
    if (clazz != null)
      img.className = clazz
    if (loading != null)
      img.loading = loading
    if (crossorigin != null)
      img.crossOrigin = crossorigin
    if (referrerPolicy != null)
      img.referrerPolicy = referrerPolicy
    if (width != null)
      img.width = width
    if (height != null)
      img.height = height
    if (decoding != null)
      img.decoding = decoding
    if (fetchPriority != null)
      img.fetchPriority = fetchPriority
    if (ismap != null)
      img.isMap = ismap
    if (usemap != null)
      img.useMap = usemap

    img.onload = () => resolve(img)
    img.onerror = reject
  })
}
```
</details>

- **Parameters**:
  - `options: UseImageOptions`
- **Return Type**: `Promise<HTMLImageElement>`
- **Calls**:
  - `resolve`
### `useImage(options: MaybeRefOrGetter<UseImageOptions>, asyncStateOptions: UseAsyncStateOptions<Shallow>): UseAsyncStateReturn<HTMLImageElement, any[], true>`

<details><summary>Code</summary>

```ts
export function useImage<Shallow extends true>(options: MaybeRefOrGetter<UseImageOptions>, asyncStateOptions: UseAsyncStateOptions<Shallow> = {}) {
  const state = useAsyncState<HTMLImageElement | undefined>(
    () => loadImage(toValue(options)),
    undefined,
    {
      resetOnExecute: true,
      ...asyncStateOptions,
    },
  )

  watch(
    () => toValue(options),
    () => state.execute(asyncStateOptions.delay),
    { deep: true },
  )

  return state
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive load an image in the browser, you can wait the result to display it or show a fallback.
 *
 * @see https://vueuse.org/useImage
 * @param options Image attributes, as used in the <img> tag
 * @param asyncStateOptions
 */
```

- **Parameters**:
  - `options: MaybeRefOrGetter<UseImageOptions>`
  - `asyncStateOptions: UseAsyncStateOptions<Shallow>`
- **Return Type**: `UseAsyncStateReturn<HTMLImageElement, any[], true>`
- **Calls**:
  - `useAsyncState (from ../useAsyncState)`
  - `loadImage`
  - `toValue (from vue)`
  - `watch (from vue)`
  - `state.execute`

---

## Interfaces

### `UseImageOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseImageOptions {
  /** Address of the resource */
  src: string
  /** Images to use in different situations, e.g., high-resolution displays, small monitors, etc. */
  srcset?: string
  /** Image sizes for different page layouts */
  sizes?: string
  /** Image alternative information */
  alt?: string
  /** Image classes */
  class?: string
  /** Image loading */
  loading?: HTMLImageElement['loading']
  /** Image CORS settings */
  crossorigin?: string
  /** Referrer policy for fetch https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Referrer-Policy */
  referrerPolicy?: HTMLImageElement['referrerPolicy']
  /** Image width */
  width?: HTMLImageElement['width']
  /** Image height */
  height?: HTMLImageElement['height']
  /** https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#decoding */
  decoding?: HTMLImageElement['decoding']
  /** Provides a hint of the relative priority to use when fetching the image */
  fetchPriority?: HTMLImageElement['fetchPriority']
  /** Provides a hint of the importance of the image */
  ismap?: HTMLImageElement['isMap']
  /** The partial URL (starting with #) of an image map associated with the element */
  usemap?: HTMLImageElement['useMap']
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `src` | `string` | ✗ |  |
| `srcset` | `string` | ✓ |  |
| `sizes` | `string` | ✓ |  |
| `alt` | `string` | ✓ |  |
| `class` | `string` | ✓ |  |
| `loading` | `HTMLImageElement['loading']` | ✓ |  |
| `crossorigin` | `string` | ✓ |  |
| `referrerPolicy` | `HTMLImageElement['referrerPolicy']` | ✓ |  |
| `width` | `HTMLImageElement['width']` | ✓ |  |
| `height` | `HTMLImageElement['height']` | ✓ |  |
| `decoding` | `HTMLImageElement['decoding']` | ✓ |  |
| `fetchPriority` | `HTMLImageElement['fetchPriority']` | ✓ |  |
| `ismap` | `HTMLImageElement['isMap']` | ✓ |  |
| `usemap` | `HTMLImageElement['useMap']` | ✓ |  |


---

## Type Aliases

### `UseImageReturn`

```ts
type UseImageReturn = ReturnType<typeof useImage>;
```


---