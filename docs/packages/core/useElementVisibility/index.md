[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 2 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useElementVisibility/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeComputedElementRef` | `../unrefElement` |
| `UseIntersectionObserverOptions` | `../useIntersectionObserver` |
| `watchOnce` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useIntersectionObserver` | `../useIntersectionObserver` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `isIntersecting` | `any` | let/var | `elementIsVisible.value` | ✗ |
| `latestTime` | `number` | let/var | `0` | ✗ |


---

## Functions

### `useElementVisibility(element: MaybeComputedElementRef, options: UseElementVisibilityOptions): any`

<details><summary>Code</summary>

```ts
export function useElementVisibility(
  element: MaybeComputedElementRef,
  options: UseElementVisibilityOptions = {},
) {
  const {
    window = defaultWindow,
    scrollTarget,
    threshold = 0,
    rootMargin,
    once = false,
  } = options
  const elementIsVisible = shallowRef(false)

  const { stop } = useIntersectionObserver(
    element,
    (intersectionObserverEntries) => {
      let isIntersecting = elementIsVisible.value

      // Get the latest value of isIntersecting based on the entry time
      let latestTime = 0
      for (const entry of intersectionObserverEntries) {
        if (entry.time >= latestTime) {
          latestTime = entry.time
          isIntersecting = entry.isIntersecting
        }
      }
      elementIsVisible.value = isIntersecting

      if (once) {
        watchOnce(elementIsVisible, () => {
          stop()
        })
      }
    },
    {
      root: scrollTarget,
      window,
      threshold,
      rootMargin: toValue(rootMargin),
    },
  )

  return elementIsVisible
}
```
</details>

- **JSDoc**:
```ts
/**
 * Tracks the visibility of an element within the viewport.
 *
 * @see https://vueuse.org/useElementVisibility
 */
```

- **Parameters**:
  - `element: MaybeComputedElementRef`
  - `options: UseElementVisibilityOptions`
- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `useIntersectionObserver (from ../useIntersectionObserver)`
  - `watchOnce (from @vueuse/shared)`
  - `stop`
  - `toValue (from vue)`
- **Internal Comments**:
```
// Get the latest value of isIntersecting based on the entry time (x2)
```


---

## Interfaces

### `UseElementVisibilityOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseElementVisibilityOptions extends ConfigurableWindow, Pick<UseIntersectionObserverOptions, 'threshold'> {
  /**
   * @see https://developer.mozilla.org/en-US/docs/Web/API/IntersectionObserver/rootMargin
   */
  rootMargin?: MaybeRefOrGetter<string>
  /**
   * The element that is used as the viewport for checking visibility of the target.
   */
  scrollTarget?: MaybeRefOrGetter<HTMLElement | undefined | null>
  /**
   * Stop tracking when element visibility changes for the first time
   *
   * @default false
   */
  once?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `rootMargin` | `MaybeRefOrGetter<string>` | ✓ |  |
| `scrollTarget` | `MaybeRefOrGetter<HTMLElement | undefined | null>` | ✓ |  |
| `once` | `boolean` | ✓ |  |


---