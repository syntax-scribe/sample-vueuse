[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 🧱 Classes | 1 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 3 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Classes](#classes)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useResizeObserver/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeComputedElementRef` | `../unrefElement` |
| `MaybeElement` | `../unrefElement` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `observer` | `ResizeObserver | undefined` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `ResizeObserver.disconnect(): void`

<details><summary>Code</summary>

```ts
disconnect(): void
```
</details>

- **Return Type**: `void`
### `ResizeObserver.observe(target: Element, options: UseResizeObserverOptions): void`

<details><summary>Code</summary>

```ts
observe(target: Element, options?: UseResizeObserverOptions): void
```
</details>

- **Parameters**:
  - `target: Element`
  - `options: UseResizeObserverOptions`
- **Return Type**: `void`
### `ResizeObserver.unobserve(target: Element): void`

<details><summary>Code</summary>

```ts
unobserve(target: Element): void
```
</details>

- **Parameters**:
  - `target: Element`
- **Return Type**: `void`
### `useResizeObserver(target: MaybeComputedElementRef | MaybeComputedElementRef[] | MaybeRefOrGetter<MaybeElement[]>, callback: ResizeObserverCallback, options: UseResizeObserverOptions): { isSupported: any; stop: () => void; }`

<details><summary>Code</summary>

```ts
export function useResizeObserver(
  target: MaybeComputedElementRef | MaybeComputedElementRef[] | MaybeRefOrGetter<MaybeElement[]>,
  callback: ResizeObserverCallback,
  options: UseResizeObserverOptions = {},
) {
  const { window = defaultWindow, ...observerOptions } = options
  let observer: ResizeObserver | undefined
  const isSupported = useSupported(() => window && 'ResizeObserver' in window)

  const cleanup = () => {
    if (observer) {
      observer.disconnect()
      observer = undefined
    }
  }

  const targets = computed(() => {
    const _targets = toValue(target)
    return Array.isArray(_targets)
      ? _targets.map(el => unrefElement(el))
      : [unrefElement(_targets)]
  })

  const stopWatch = watch(
    targets,
    (els) => {
      cleanup()
      if (isSupported.value && window) {
        observer = new ResizeObserver(callback)
        for (const _el of els) {
          if (_el)
            observer!.observe(_el, observerOptions)
        }
      }
    },
    { immediate: true, flush: 'post' },
  )

  const stop = () => {
    cleanup()
    stopWatch()
  }

  tryOnScopeDispose(stop)

  return {
    isSupported,
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reports changes to the dimensions of an Element's content or the border-box
 *
 * @see https://vueuse.org/useResizeObserver
 * @param target
 * @param callback
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeComputedElementRef | MaybeComputedElementRef[] | MaybeRefOrGetter<MaybeElement[]>`
  - `callback: ResizeObserverCallback`
  - `options: UseResizeObserverOptions`
- **Return Type**: `{ isSupported: any; stop: () => void; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `observer.disconnect`
  - `computed (from vue)`
  - `toValue (from vue)`
  - `Array.isArray`
  - `_targets.map`
  - `unrefElement (from ../unrefElement)`
  - `watch (from vue)`
  - `cleanup`
  - `observer!.observe`
  - `stopWatch`
  - `tryOnScopeDispose (from @vueuse/shared)`
### `cleanup(): void`

<details><summary>Code</summary>

```ts
() => {
    if (observer) {
      observer.disconnect()
      observer = undefined
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `observer.disconnect`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    cleanup()
    stopWatch()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `cleanup`
  - `stopWatch`

---

## Classes

### `ResizeObserver`

<details><summary>Class Code</summary>

```ts
declare class ResizeObserver {
  constructor(callback: ResizeObserverCallback)
  disconnect(): void
  observe(target: Element, options?: UseResizeObserverOptions): void
  unobserve(target: Element): void
}
```
</details>

#### Methods

##### `disconnect(): void`

<details><summary>Code</summary>

```ts
disconnect(): void
```
</details>

##### `observe(target: Element, options: UseResizeObserverOptions): void`

<details><summary>Code</summary>

```ts
observe(target: Element, options?: UseResizeObserverOptions): void
```
</details>

##### `unobserve(target: Element): void`

<details><summary>Code</summary>

```ts
unobserve(target: Element): void
```
</details>


---

## Interfaces

### `ResizeObserverSize`

<details><summary>Interface Code</summary>

```ts
export interface ResizeObserverSize {
  readonly inlineSize: number
  readonly blockSize: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `inlineSize` | `number` | ✗ |  |
| `blockSize` | `number` | ✗ |  |

### `ResizeObserverEntry`

<details><summary>Interface Code</summary>

```ts
export interface ResizeObserverEntry {
  readonly target: Element
  readonly contentRect: DOMRectReadOnly
  readonly borderBoxSize: ReadonlyArray<ResizeObserverSize>
  readonly contentBoxSize: ReadonlyArray<ResizeObserverSize>
  readonly devicePixelContentBoxSize: ReadonlyArray<ResizeObserverSize>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `target` | `Element` | ✗ |  |
| `contentRect` | `DOMRectReadOnly` | ✗ |  |
| `borderBoxSize` | `ReadonlyArray<ResizeObserverSize>` | ✗ |  |
| `contentBoxSize` | `ReadonlyArray<ResizeObserverSize>` | ✗ |  |
| `devicePixelContentBoxSize` | `ReadonlyArray<ResizeObserverSize>` | ✗ |  |

### `UseResizeObserverOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseResizeObserverOptions extends ConfigurableWindow {
  /**
   * Sets which box model the observer will observe changes to. Possible values
   * are `content-box` (the default), `border-box` and `device-pixel-content-box`.
   *
   * @default 'content-box'
   */
  box?: ResizeObserverBoxOptions
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `box` | `ResizeObserverBoxOptions` | ✓ |  |


---

## Type Aliases

### `ResizeObserverCallback`

```ts
type ResizeObserverCallback = (entries: ReadonlyArray<ResizeObserverEntry>, observer: ResizeObserver) => void;
```

### `UseResizeObserverReturn`

```ts
type UseResizeObserverReturn = ReturnType<typeof useResizeObserver>;
```


---