[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 17
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useIntersectionObserver/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeComputedElementRef` | `../unrefElement` |
| `MaybeElement` | `../unrefElement` |
| `noop` | `@vueuse/shared` |
| `notNullish` | `@vueuse/shared` |
| `toArray` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useIntersectionObserver(target: MaybeComputedElementRef | MaybeRefOrGetter<MaybeElement[]> | MaybeComputedElementRef[], callback: IntersectionObserverCallback, options: UseIntersectionObserverOptions): UseIntersectionObserverReturn`

<details><summary>Code</summary>

```ts
export function useIntersectionObserver(
  target: MaybeComputedElementRef | MaybeRefOrGetter<MaybeElement[]> | MaybeComputedElementRef[],
  callback: IntersectionObserverCallback,
  options: UseIntersectionObserverOptions = {},
): UseIntersectionObserverReturn {
  const {
    root,
    rootMargin = '0px',
    threshold = 0,
    window = defaultWindow,
    immediate = true,
  } = options

  const isSupported = useSupported(() => window && 'IntersectionObserver' in window)
  const targets = computed(() => {
    const _target = toValue(target)
    return toArray(_target).map(unrefElement).filter(notNullish)
  })

  let cleanup = noop
  const isActive = shallowRef(immediate)

  const stopWatch = isSupported.value
    ? watch(
        () => [targets.value, unrefElement(root as MaybeComputedElementRef), isActive.value] as const,
        ([targets, root]) => {
          cleanup()
          if (!isActive.value)
            return

          if (!targets.length)
            return

          const observer = new IntersectionObserver(
            callback,
            {
              root: unrefElement(root),
              rootMargin,
              threshold,
            },
          )

          targets.forEach(el => el && observer.observe(el))

          cleanup = () => {
            observer.disconnect()
            cleanup = noop
          }
        },
        { immediate, flush: 'post' },
      )
    : noop

  const stop = () => {
    cleanup()
    stopWatch()
    isActive.value = false
  }

  tryOnScopeDispose(stop)

  return {
    isSupported,
    isActive,
    pause() {
      cleanup()
      isActive.value = false
    },
    resume() {
      isActive.value = true
    },
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Detects that a target element's visibility.
 *
 * @see https://vueuse.org/useIntersectionObserver
 * @param target
 * @param callback
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeComputedElementRef | MaybeRefOrGetter<MaybeElement[]> | MaybeComputedElementRef[]`
  - `callback: IntersectionObserverCallback`
  - `options: UseIntersectionObserverOptions`
- **Return Type**: `UseIntersectionObserverReturn`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `computed (from vue)`
  - `toValue (from vue)`
  - `toArray(_target).map(unrefElement).filter`
  - `shallowRef (from vue)`
  - `watch (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `cleanup`
  - `targets.forEach`
  - `observer.observe`
  - `observer.disconnect`
  - `stopWatch`
  - `tryOnScopeDispose (from @vueuse/shared)`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    cleanup()
    stopWatch()
    isActive.value = false
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `cleanup`
  - `stopWatch`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseIntersectionObserverOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseIntersectionObserverOptions extends ConfigurableWindow {
  /**
   * Start the IntersectionObserver immediately on creation
   *
   * @default true
   */
  immediate?: boolean

  /**
   * The Element or Document whose bounds are used as the bounding box when testing for intersection.
   */
  root?: MaybeComputedElementRef | Document

  /**
   * A string which specifies a set of offsets to add to the root's bounding_box when calculating intersections.
   */
  rootMargin?: string

  /**
   * Either a single number or an array of numbers between 0.0 and 1.
   * @default 0
   */
  threshold?: number | number[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |
| `root` | `MaybeComputedElementRef | Document` | ✓ |  |
| `rootMargin` | `string` | ✓ |  |
| `threshold` | `number | number[]` | ✓ |  |

### `UseIntersectionObserverReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseIntersectionObserverReturn extends Pausable {
  isSupported: ComputedRef<boolean>
  stop: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `stop` | `() => void` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---