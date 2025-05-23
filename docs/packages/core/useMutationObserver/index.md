[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 13
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useMutationObserver/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeComputedElementRef` | `../unrefElement` |
| `MaybeElement` | `../unrefElement` |
| `notNullish` | `@vueuse/shared` |
| `toArray` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useMutationObserver(target: MaybeComputedElementRef | MaybeComputedElementRef[] | MaybeRefOrGetter<MaybeElement[]>, callback: MutationCallback, options: UseMutationObserverOptions): { isSupported: any; stop: () => void; takeRecords: () => MutationRecord[]; }`

<details><summary>Code</summary>

```ts
export function useMutationObserver(
  target: MaybeComputedElementRef | MaybeComputedElementRef[] | MaybeRefOrGetter<MaybeElement[]>,
  callback: MutationCallback,
  options: UseMutationObserverOptions = {},
) {
  const { window = defaultWindow, ...mutationOptions } = options
  let observer: MutationObserver | undefined
  const isSupported = useSupported(() => window && 'MutationObserver' in window)

  const cleanup = () => {
    if (observer) {
      observer.disconnect()
      observer = undefined
    }
  }

  const targets = computed(() => {
    const value = toValue(target)
    const items = toArray(value)
      .map(unrefElement)
      .filter(notNullish)
    return new Set(items)
  })

  const stopWatch = watch(
    () => targets.value,
    (targets) => {
      cleanup()

      if (isSupported.value && targets.size) {
        observer = new MutationObserver(callback)
        targets.forEach(el => observer!.observe(el, mutationOptions))
      }
    },
    { immediate: true, flush: 'post' },
  )

  const takeRecords = () => {
    return observer?.takeRecords()
  }

  const stop = () => {
    stopWatch()
    cleanup()
  }

  tryOnScopeDispose(stop)

  return {
    isSupported,
    stop,
    takeRecords,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Watch for changes being made to the DOM tree.
 *
 * @see https://vueuse.org/useMutationObserver
 * @see https://developer.mozilla.org/en-US/docs/Web/API/MutationObserver MutationObserver MDN
 * @param target
 * @param callback
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeComputedElementRef | MaybeComputedElementRef[] | MaybeRefOrGetter<MaybeElement[]>`
  - `callback: MutationCallback`
  - `options: UseMutationObserverOptions`
- **Return Type**: `{ isSupported: any; stop: () => void; takeRecords: () => MutationRecord[]; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `observer.disconnect`
  - `computed (from vue)`
  - `toValue (from vue)`
  - `toArray(value)
      .map(unrefElement)
      .filter`
  - `watch (from vue)`
  - `cleanup`
  - `targets.forEach`
  - `observer!.observe`
  - `observer?.takeRecords`
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
### `takeRecords(): MutationRecord[]`

<details><summary>Code</summary>

```ts
() => {
    return observer?.takeRecords()
  }
```
</details>

- **Return Type**: `MutationRecord[]`
- **Calls**:
  - `observer?.takeRecords`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    stopWatch()
    cleanup()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stopWatch`
  - `cleanup`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseMutationObserverOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseMutationObserverOptions extends MutationObserverInit, ConfigurableWindow {}
```
</details>


---

## Type Aliases

### `UseMutationObserverReturn`

```ts
type UseMutationObserverReturn = ReturnType<typeof useMutationObserver>;
```


---