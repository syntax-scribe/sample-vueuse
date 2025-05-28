[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 15 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 11 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 6 |
| 📐 Interfaces | 8 |
| 📑 Type Aliases | 7 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useVirtualList/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `StyleValue` | `vue` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `useElementSize` | `../useElementSize` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `sum` | `number` | let/var | `0` | ✗ |
| `capacity` | `number` | let/var | `0` | ✗ |
| `sum` | `number` | let/var | `0` | ✗ |
| `offset` | `number` | let/var | `0` | ✗ |
| `element` | `any` | const | `containerRef.value` | ✗ |
| `from` | `number` | const | `offset - overscan` | ✗ |
| `to` | `number` | const | `offset + viewCapacity + overscan` | ✗ |
| `size` | `number` | const | `index * itemSize` | ✗ |
| `scrollToDictionaryForElementScrollKey` | `{ readonly horizontal: "scrollLeft"; readonly vertical: "scrollTop"; }` | const | `{
  horizontal: 'scrollLeft',
  vertical: 'scrollTop',
} as const` | ✗ |
| `containerStyle` | `StyleValue` | const | `{ overflowX: 'auto' }` | ✗ |
| `containerStyle` | `StyleValue` | const | `{ overflowY: 'auto' }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useVirtualList(list: MaybeRef<readonly T[]>, options: UseVirtualListOptions): UseVirtualListReturn<T>`

<details><summary>Code</summary>

```ts
export function useVirtualList<T = any>(list: MaybeRef<readonly T[]>, options: UseVirtualListOptions): UseVirtualListReturn<T> {
  const { containerStyle, wrapperProps, scrollTo, calculateRange, currentList, containerRef } = 'itemHeight' in options
    ? useVerticalVirtualList(options, list)
    : useHorizontalVirtualList(options, list)

  return {
    list: currentList,
    scrollTo,
    containerProps: {
      ref: containerRef,
      onScroll: () => {
        calculateRange()
      },
      style: containerStyle,
    },
    wrapperProps,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Please consider using [`vue-virtual-scroller`](https://github.com/Akryum/vue-virtual-scroller) if you are looking for more features.
 */
```

- **Parameters**:
  - `list: MaybeRef<readonly T[]>`
  - `options: UseVirtualListOptions`
- **Return Type**: `UseVirtualListReturn<T>`
- **Calls**:
  - `useVerticalVirtualList`
  - `useHorizontalVirtualList`
  - `calculateRange`
### `onScroll(): void`

<details><summary>Code</summary>

```ts
() => {
        calculateRange()
      }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `calculateRange`
### `onScroll(): void`

<details><summary>Code</summary>

```ts
() => {
        calculateRange()
      }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `calculateRange`
### `onScroll(): void`

<details><summary>Code</summary>

```ts
() => {
        calculateRange()
      }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `calculateRange`
### `onScroll(): void`

<details><summary>Code</summary>

```ts
() => {
        calculateRange()
      }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `calculateRange`
### `useVirtualListResources(list: MaybeRef<readonly T[]>): UseVirtualListResources<T>`

<details><summary>Code</summary>

```ts
function useVirtualListResources<T>(list: MaybeRef<readonly T[]>): UseVirtualListResources<T> {
  const containerRef = shallowRef<HTMLElement | null>(null)
  const size = useElementSize(containerRef)

  const currentList: Ref<UseVirtualListItem<T>[]> = deepRef([])
  const source = shallowRef(list)

  const state: Ref<{ start: number, end: number }> = deepRef({ start: 0, end: 10 })

  return { state, source, currentList, size, containerRef }
}
```
</details>

- **Parameters**:
  - `list: MaybeRef<readonly T[]>`
- **Return Type**: `UseVirtualListResources<T>`
- **Calls**:
  - `shallowRef (from vue)`
  - `useElementSize (from ../useElementSize)`
  - `deepRef (from vue)`
### `createGetViewCapacity(state: UseVirtualListResources<T>['state'], source: UseVirtualListResources<T>['source'], itemSize: UseVirtualListItemSize): (containerSize: number) => number`

<details><summary>Code</summary>

```ts
function createGetViewCapacity<T>(state: UseVirtualListResources<T>['state'], source: UseVirtualListResources<T>['source'], itemSize: UseVirtualListItemSize) {
  return (containerSize: number) => {
    if (typeof itemSize === 'number')
      return Math.ceil(containerSize / itemSize)

    const { start = 0 } = state.value
    let sum = 0
    let capacity = 0
    for (let i = start; i < source.value.length; i++) {
      const size = itemSize(i)
      sum += size
      capacity = i
      if (sum > containerSize)
        break
    }
    return capacity - start
  }
}
```
</details>

- **Parameters**:
  - `state: UseVirtualListResources<T>['state']`
  - `source: UseVirtualListResources<T>['source']`
  - `itemSize: UseVirtualListItemSize`
- **Return Type**: `(containerSize: number) => number`
- **Calls**:
  - `Math.ceil`
  - `itemSize`
### `createGetOffset(source: UseVirtualListResources<T>['source'], itemSize: UseVirtualListItemSize): (scrollDirection: number) => number`

<details><summary>Code</summary>

```ts
function createGetOffset<T>(source: UseVirtualListResources<T>['source'], itemSize: UseVirtualListItemSize) {
  return (scrollDirection: number) => {
    if (typeof itemSize === 'number')
      return Math.floor(scrollDirection / itemSize) + 1

    let sum = 0
    let offset = 0

    for (let i = 0; i < source.value.length; i++) {
      const size = itemSize(i)
      sum += size
      if (sum >= scrollDirection) {
        offset = i
        break
      }
    }
    return offset + 1
  }
}
```
</details>

- **Parameters**:
  - `source: UseVirtualListResources<T>['source']`
  - `itemSize: UseVirtualListItemSize`
- **Return Type**: `(scrollDirection: number) => number`
- **Calls**:
  - `Math.floor`
  - `itemSize`
### `createCalculateRange(type: 'horizontal' | 'vertical', overscan: number, getOffset: ReturnType<typeof createGetOffset>, getViewCapacity: ReturnType<typeof createGetViewCapacity>, { containerRef, state, currentList, source }: UseVirtualListResources<T>): () => void`

<details><summary>Code</summary>

```ts
function createCalculateRange<T>(type: 'horizontal' | 'vertical', overscan: number, getOffset: ReturnType<typeof createGetOffset>, getViewCapacity: ReturnType<typeof createGetViewCapacity>, { containerRef, state, currentList, source }: UseVirtualListResources<T>) {
  return () => {
    const element = containerRef.value
    if (element) {
      const offset = getOffset(type === 'vertical' ? element.scrollTop : element.scrollLeft)
      const viewCapacity = getViewCapacity(type === 'vertical' ? element.clientHeight : element.clientWidth)

      const from = offset - overscan
      const to = offset + viewCapacity + overscan
      state.value = {
        start: from < 0 ? 0 : from,
        end: to > source.value.length
          ? source.value.length
          : to,
      }
      currentList.value = source.value
        .slice(state.value.start, state.value.end)
        .map((ele, index) => ({
          data: ele,
          index: index + state.value.start,
        }))
    }
  }
}
```
</details>

- **Parameters**:
  - `type: 'horizontal' | 'vertical'`
  - `overscan: number`
  - `getOffset: ReturnType<typeof createGetOffset>`
  - `getViewCapacity: ReturnType<typeof createGetViewCapacity>`
  - `{ containerRef, state, currentList, source }: UseVirtualListResources<T>`
- **Return Type**: `() => void`
- **Calls**:
  - `getOffset`
  - `getViewCapacity`
  - `source.value
        .slice(state.value.start, state.value.end)
        .map`
### `createGetDistance(itemSize: UseVirtualListItemSize, source: UseVirtualListResources<T>['source']): (index: number) => any`

<details><summary>Code</summary>

```ts
function createGetDistance<T>(itemSize: UseVirtualListItemSize, source: UseVirtualListResources<T>['source']) {
  return (index: number) => {
    if (typeof itemSize === 'number') {
      const size = index * itemSize
      return size
    }

    const size = source.value
      .slice(0, index)
      .reduce((sum, _, i) => sum + itemSize(i), 0)

    return size
  }
}
```
</details>

- **Parameters**:
  - `itemSize: UseVirtualListItemSize`
  - `source: UseVirtualListResources<T>['source']`
- **Return Type**: `(index: number) => any`
- **Calls**:
  - `source.value
      .slice(0, index)
      .reduce`
  - `itemSize`
### `useWatchForSizes(size: UseVirtualElementSizes, list: MaybeRef<readonly T[]>, containerRef: Ref<HTMLElement | null>, calculateRange: () => void): void`

<details><summary>Code</summary>

```ts
function useWatchForSizes<T>(size: UseVirtualElementSizes, list: MaybeRef<readonly T[]>, containerRef: Ref<HTMLElement | null>, calculateRange: () => void) {
  watch([size.width, size.height, list, containerRef], () => {
    calculateRange()
  })
}
```
</details>

- **Parameters**:
  - `size: UseVirtualElementSizes`
  - `list: MaybeRef<readonly T[]>`
  - `containerRef: Ref<HTMLElement | null>`
  - `calculateRange: () => void`
- **Return Type**: `void`
- **Calls**:
  - `watch (from vue)`
  - `calculateRange`
### `createComputedTotalSize(itemSize: UseVirtualListItemSize, source: UseVirtualListResources<T>['source']): any`

<details><summary>Code</summary>

```ts
function createComputedTotalSize<T>(itemSize: UseVirtualListItemSize, source: UseVirtualListResources<T>['source']) {
  return computed(() => {
    if (typeof itemSize === 'number')
      return source.value.length * itemSize

    return source.value.reduce((sum, _, index) => sum + itemSize(index), 0)
  })
}
```
</details>

- **Parameters**:
  - `itemSize: UseVirtualListItemSize`
  - `source: UseVirtualListResources<T>['source']`
- **Return Type**: `any`
- **Calls**:
  - `computed (from vue)`
  - `source.value.reduce`
  - `itemSize`
### `createScrollTo(type: 'horizontal' | 'vertical', calculateRange: () => void, getDistance: ReturnType<typeof createGetDistance>, containerRef: UseVirtualListResources<T>['containerRef']): (index: number) => void`

<details><summary>Code</summary>

```ts
function createScrollTo<T>(type: 'horizontal' | 'vertical', calculateRange: () => void, getDistance: ReturnType<typeof createGetDistance>, containerRef: UseVirtualListResources<T>['containerRef']) {
  return (index: number) => {
    if (containerRef.value) {
      containerRef.value[scrollToDictionaryForElementScrollKey[type]] = getDistance(index)
      calculateRange()
    }
  }
}
```
</details>

- **Parameters**:
  - `type: 'horizontal' | 'vertical'`
  - `calculateRange: () => void`
  - `getDistance: ReturnType<typeof createGetDistance>`
  - `containerRef: UseVirtualListResources<T>['containerRef']`
- **Return Type**: `(index: number) => void`
- **Calls**:
  - `getDistance`
  - `calculateRange`
### `useHorizontalVirtualList(options: UseHorizontalVirtualListOptions, list: MaybeRef<readonly T[]>): { scrollTo: (index: number) => void; calculateRange: () => void; wrapperProps: any; containerStyle: StyleValue; currentList: Ref<UseVirtualListArray<T>>; containerRef: Ref<HTMLElement>; }`

<details><summary>Code</summary>

```ts
function useHorizontalVirtualList<T>(options: UseHorizontalVirtualListOptions, list: MaybeRef<readonly T[]>) {
  const resources = useVirtualListResources(list)
  const { state, source, currentList, size, containerRef } = resources
  const containerStyle: StyleValue = { overflowX: 'auto' }

  const { itemWidth, overscan = 5 } = options

  const getViewCapacity = createGetViewCapacity(state, source, itemWidth)

  const getOffset = createGetOffset(source, itemWidth)

  const calculateRange = createCalculateRange('horizontal', overscan, getOffset, getViewCapacity, resources)

  const getDistanceLeft = createGetDistance(itemWidth, source)

  const offsetLeft = computed(() => getDistanceLeft(state.value.start))

  const totalWidth = createComputedTotalSize(itemWidth, source)

  useWatchForSizes(size, list, containerRef, calculateRange)

  const scrollTo = createScrollTo('horizontal', calculateRange, getDistanceLeft, containerRef)

  const wrapperProps = computed(() => {
    return {
      style: {
        height: '100%',
        width: `${totalWidth.value - offsetLeft.value}px`,
        marginLeft: `${offsetLeft.value}px`,
        display: 'flex',
      },
    }
  })

  return {
    scrollTo,
    calculateRange,
    wrapperProps,
    containerStyle,
    currentList,
    containerRef,
  }
}
```
</details>

- **Parameters**:
  - `options: UseHorizontalVirtualListOptions`
  - `list: MaybeRef<readonly T[]>`
- **Return Type**: `{ scrollTo: (index: number) => void; calculateRange: () => void; wrapperProps: any; containerStyle: StyleValue; currentList: Ref<UseVirtualListArray<T>>; containerRef: Ref<HTMLElement>; }`
- **Calls**:
  - `useVirtualListResources`
  - `createGetViewCapacity`
  - `createGetOffset`
  - `createCalculateRange`
  - `createGetDistance`
  - `computed (from vue)`
  - `getDistanceLeft`
  - `createComputedTotalSize`
  - `useWatchForSizes`
  - `createScrollTo`
### `useVerticalVirtualList(options: UseVerticalVirtualListOptions, list: MaybeRef<readonly T[]>): { calculateRange: () => void; scrollTo: (index: number) => void; containerStyle: StyleValue; wrapperProps: any; currentList: Ref<UseVirtualListArray<T>>; containerRef: Ref<HTMLElement>; }`

<details><summary>Code</summary>

```ts
function useVerticalVirtualList<T>(options: UseVerticalVirtualListOptions, list: MaybeRef<readonly T[]>) {
  const resources = useVirtualListResources(list)

  const { state, source, currentList, size, containerRef } = resources

  const containerStyle: StyleValue = { overflowY: 'auto' }

  const { itemHeight, overscan = 5 } = options

  const getViewCapacity = createGetViewCapacity(state, source, itemHeight)

  const getOffset = createGetOffset(source, itemHeight)

  const calculateRange = createCalculateRange('vertical', overscan, getOffset, getViewCapacity, resources)

  const getDistanceTop = createGetDistance(itemHeight, source)

  const offsetTop = computed(() => getDistanceTop(state.value.start))

  const totalHeight = createComputedTotalSize(itemHeight, source)

  useWatchForSizes(size, list, containerRef, calculateRange)

  const scrollTo = createScrollTo('vertical', calculateRange, getDistanceTop, containerRef)

  const wrapperProps = computed(() => {
    return {
      style: {
        width: '100%',
        height: `${totalHeight.value - offsetTop.value}px`,
        marginTop: `${offsetTop.value}px`,
      },
    }
  })

  return {
    calculateRange,
    scrollTo,
    containerStyle,
    wrapperProps,
    currentList,
    containerRef,
  }
}
```
</details>

- **Parameters**:
  - `options: UseVerticalVirtualListOptions`
  - `list: MaybeRef<readonly T[]>`
- **Return Type**: `{ calculateRange: () => void; scrollTo: (index: number) => void; containerStyle: StyleValue; wrapperProps: any; currentList: Ref<UseVirtualListArray<T>>; containerRef: Ref<HTMLElement>; }`
- **Calls**:
  - `useVirtualListResources`
  - `createGetViewCapacity`
  - `createGetOffset`
  - `createCalculateRange`
  - `createGetDistance`
  - `computed (from vue)`
  - `getDistanceTop`
  - `createComputedTotalSize`
  - `useWatchForSizes`
  - `createScrollTo`

---

## Interfaces

### `UseHorizontalVirtualListOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseHorizontalVirtualListOptions extends UseVirtualListOptionsBase {

  /**
   * item width, accept a pixel value or a function that returns the width
   *
   * @default 0
   */
  itemWidth: UseVirtualListItemSize

}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `itemWidth` | `UseVirtualListItemSize` | ✗ |  |

### `UseVerticalVirtualListOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseVerticalVirtualListOptions extends UseVirtualListOptionsBase {
  /**
   * item height, accept a pixel value or a function that returns the height
   *
   * @default 0
   */
  itemHeight: UseVirtualListItemSize
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `itemHeight` | `UseVirtualListItemSize` | ✗ |  |

### `UseVirtualListOptionsBase`

<details><summary>Interface Code</summary>

```ts
export interface UseVirtualListOptionsBase {
  /**
   * the extra buffer items outside of the view area
   *
   * @default 5
   */
  overscan?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `overscan` | `number` | ✓ |  |

### `UseVirtualListItem<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseVirtualListItem<T> {
  data: T
  index: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `data` | `T` | ✗ |  |
| `index` | `number` | ✗ |  |

### `UseVirtualListReturn<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseVirtualListReturn<T> {
  list: Ref<UseVirtualListItem<T>[]>
  scrollTo: (index: number) => void

  containerProps: {
    ref: Ref<HTMLElement | null>
    onScroll: () => void
    style: StyleValue
  }
  wrapperProps: ComputedRef<{
    style: {
      width: string
      height: string
      marginTop: string
    } | {
      width: string
      height: string
      marginLeft: string
      display: string
    }
  }>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `list` | `Ref<UseVirtualListItem<T>[]>` | ✗ |  |
| `scrollTo` | `(index: number) => void` | ✗ |  |
| `containerProps` | `{
    ref: Ref<HTMLElement | null>
    onScroll: () => void
    style: StyleValue
  }` | ✗ |  |
| `wrapperProps` | `ComputedRef<{
    style: {
      width: string
      height: string
      marginTop: string
    } | {
      width: string
      height: string
      marginLeft: string
      display: string
    }
  }>` | ✗ |  |

### `UseVirtualElementSizes`

<details><summary>Interface Code</summary>

```ts
interface UseVirtualElementSizes {
  width: Ref<number>
  height: Ref<number>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `width` | `Ref<number>` | ✗ |  |
| `height` | `Ref<number>` | ✗ |  |

### `UseVirtualListState`

<details><summary>Interface Code</summary>

```ts
interface UseVirtualListState { start: number, end: number }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `start` | `number` | ✗ |  |
| `end` | `number` | ✗ |  |

### `UseVirtualListResources<T>`

<details><summary>Interface Code</summary>

```ts
interface UseVirtualListResources<T> {
  state: RefState
  source: UseVirtualListSource<T>
  currentList: UseVirtualListRefArray<T>
  size: UseVirtualElementSizes
  containerRef: UseVirtualListContainerRef
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `state` | `RefState` | ✗ |  |
| `source` | `UseVirtualListSource<T>` | ✗ |  |
| `currentList` | `UseVirtualListRefArray<T>` | ✗ |  |
| `size` | `UseVirtualElementSizes` | ✗ |  |
| `containerRef` | `UseVirtualListContainerRef` | ✗ |  |


---

## Type Aliases

### `UseVirtualListItemSize`

```ts
type UseVirtualListItemSize = number | ((index: number) => number);
```

### `UseVirtualListOptions`

```ts
type UseVirtualListOptions = UseHorizontalVirtualListOptions | UseVerticalVirtualListOptions;
```

### `UseVirtualListContainerRef`

```ts
type UseVirtualListContainerRef = Ref<HTMLElement | null>;
```

### `UseVirtualListArray<T>`

```ts
type UseVirtualListArray<T> = UseVirtualListItem<T>[];
```

### `UseVirtualListRefArray<T>`

```ts
type UseVirtualListRefArray<T> = Ref<UseVirtualListArray<T>>;
```

### `UseVirtualListSource<T>`

```ts
type UseVirtualListSource<T> = Ref<readonly T[]> | ShallowRef<readonly T[]>;
```

### `RefState`

```ts
type RefState = Ref<UseVirtualListState>;
```


---