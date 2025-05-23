[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 14
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useInfiniteScroll/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Awaitable` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `UnwrapNestedRefs` | `vue` |
| `UseScrollOptions` | `../useScroll` |
| `tryOnUnmounted` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `nextTick` | `vue` |
| `reactive` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `resolveElement` | `../_resolve-element` |
| `useElementVisibility` | `../useElementVisibility` |
| `useScroll` | `../useScroll` |


---

## Functions

### `useInfiniteScroll(element: MaybeRefOrGetter<T>, onLoadMore: (state: UnwrapNestedRefs<ReturnType<typeof useScroll>>) => Awaitable<void>, options: UseInfiniteScrollOptions<T>): { isLoading: any; reset(): void; }`

<details><summary>Code</summary>

```ts
export function useInfiniteScroll<T extends InfiniteScrollElement>(
  element: MaybeRefOrGetter<T>,
  onLoadMore: (state: UnwrapNestedRefs<ReturnType<typeof useScroll>>) => Awaitable<void>,
  options: UseInfiniteScrollOptions<T> = {},
) {
  const {
    direction = 'bottom',
    interval = 100,
    canLoadMore = () => true,
  } = options

  const state = reactive(useScroll(
    element,
    {
      ...options,
      offset: {
        [direction]: options.distance ?? 0,
        ...options.offset,
      },
    },
  ))

  const promise = deepRef<any>()
  const isLoading = computed(() => !!promise.value)

  // Document and Window cannot be observed by IntersectionObserver
  const observedElement = computed<HTMLElement | SVGElement | null | undefined>(() => {
    return resolveElement(toValue(element))
  })

  const isElementVisible = useElementVisibility(observedElement)

  function checkAndLoad() {
    state.measure()

    if (!observedElement.value || !isElementVisible.value || !canLoadMore(observedElement.value as T))
      return

    const { scrollHeight, clientHeight, scrollWidth, clientWidth } = observedElement.value as HTMLElement
    const isNarrower = (direction === 'bottom' || direction === 'top')
      ? scrollHeight <= clientHeight
      : scrollWidth <= clientWidth

    if (state.arrivedState[direction] || isNarrower) {
      if (!promise.value) {
        promise.value = Promise.all([
          onLoadMore(state),
          new Promise(resolve => setTimeout(resolve, interval)),
        ])
          .finally(() => {
            promise.value = null
            nextTick(() => checkAndLoad())
          })
      }
    }
  }

  const stop = watch(
    () => [state.arrivedState[direction], isElementVisible.value],
    checkAndLoad,
    { immediate: true },
  )

  tryOnUnmounted(stop)

  return {
    isLoading,
    reset() {
      nextTick(() => checkAndLoad())
    },
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive infinite scroll.
 *
 * @see https://vueuse.org/useInfiniteScroll
 */
```

- **Parameters**:
  - `element: MaybeRefOrGetter<T>`
  - `onLoadMore: (state: UnwrapNestedRefs<ReturnType<typeof useScroll>>) => Awaitable<void>`
  - `options: UseInfiniteScrollOptions<T>`
- **Return Type**: `{ isLoading: any; reset(): void; }`
- **Calls**:
  - `reactive (from vue)`
  - `useScroll (from ../useScroll)`
  - `deepRef (from vue)`
  - `computed (from vue)`
  - `resolveElement (from ../_resolve-element)`
  - `toValue (from vue)`
  - `useElementVisibility (from ../useElementVisibility)`
  - `state.measure`
  - `canLoadMore`
  - `Promise.all([
          onLoadMore(state),
          new Promise(resolve => setTimeout(resolve, interval)),
        ])
          .finally`
  - `nextTick (from vue)`
  - `checkAndLoad`
  - `watch (from vue)`
  - `tryOnUnmounted (from @vueuse/shared)`
- **Internal Comments**:
```
// Document and Window cannot be observed by IntersectionObserver (x2)
```

### `checkAndLoad(): void`

<details><summary>Code</summary>

```ts
function checkAndLoad() {
    state.measure()

    if (!observedElement.value || !isElementVisible.value || !canLoadMore(observedElement.value as T))
      return

    const { scrollHeight, clientHeight, scrollWidth, clientWidth } = observedElement.value as HTMLElement
    const isNarrower = (direction === 'bottom' || direction === 'top')
      ? scrollHeight <= clientHeight
      : scrollWidth <= clientWidth

    if (state.arrivedState[direction] || isNarrower) {
      if (!promise.value) {
        promise.value = Promise.all([
          onLoadMore(state),
          new Promise(resolve => setTimeout(resolve, interval)),
        ])
          .finally(() => {
            promise.value = null
            nextTick(() => checkAndLoad())
          })
      }
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `state.measure`
  - `canLoadMore`
  - `Promise.all([
          onLoadMore(state),
          new Promise(resolve => setTimeout(resolve, interval)),
        ])
          .finally`
  - `nextTick (from vue)`
  - `checkAndLoad`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseInfiniteScrollOptions<T extends InfiniteScrollElement = InfiniteScrollElement>`

<details><summary>Interface Code</summary>

```ts
export interface UseInfiniteScrollOptions<T extends InfiniteScrollElement = InfiniteScrollElement> extends UseScrollOptions {
  /**
   * The minimum distance between the bottom of the element and the bottom of the viewport
   *
   * @default 0
   */
  distance?: number

  /**
   * The direction in which to listen the scroll.
   *
   * @default 'bottom'
   */
  direction?: 'top' | 'bottom' | 'left' | 'right'

  /**
   * The interval time between two load more (to avoid too many invokes).
   *
   * @default 100
   */
  interval?: number

  /**
   * A function that determines whether more content can be loaded for a specific element.
   * Should return `true` if loading more content is allowed for the given element,
   * and `false` otherwise.
   */
  canLoadMore?: (el: T) => boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `distance` | `number` | ✓ |  |
| `direction` | `'top' | 'bottom' | 'left' | 'right'` | ✓ |  |
| `interval` | `number` | ✓ |  |
| `canLoadMore` | `(el: T) => boolean` | ✓ |  |


---

## Type Aliases

### `InfiniteScrollElement`

```ts
type InfiniteScrollElement = HTMLElement | SVGElement | Window | Document | null | undefined;
```


---