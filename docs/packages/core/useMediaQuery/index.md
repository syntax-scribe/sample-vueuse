[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useMediaQuery/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `pxValue` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watchEffect` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSSRWidth` | `../useSSRWidth` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useMediaQuery(query: MaybeRefOrGetter<string>, options: ConfigurableWindow & { ssrWidth?: number }): any`

<details><summary>Code</summary>

```ts
export function useMediaQuery(query: MaybeRefOrGetter<string>, options: ConfigurableWindow & { ssrWidth?: number } = {}) {
  const { window = defaultWindow, ssrWidth = useSSRWidth() } = options
  const isSupported = useSupported(() => window && 'matchMedia' in window && typeof window.matchMedia === 'function')

  const ssrSupport = shallowRef(typeof ssrWidth === 'number')

  const mediaQuery = shallowRef<MediaQueryList>()
  const matches = shallowRef(false)

  const handler = (event: MediaQueryListEvent) => {
    matches.value = event.matches
  }

  watchEffect(() => {
    if (ssrSupport.value) {
      // Exit SSR support on mounted if window available
      ssrSupport.value = !isSupported.value

      const queryStrings = toValue(query).split(',')
      matches.value = queryStrings.some((queryString) => {
        const not = queryString.includes('not all')
        const minWidth = queryString.match(/\(\s*min-width:\s*(-?\d+(?:\.\d*)?[a-z]+\s*)\)/)
        const maxWidth = queryString.match(/\(\s*max-width:\s*(-?\d+(?:\.\d*)?[a-z]+\s*)\)/)
        let res = Boolean(minWidth || maxWidth)
        if (minWidth && res) {
          res = ssrWidth! >= pxValue(minWidth[1])
        }
        if (maxWidth && res) {
          res = ssrWidth! <= pxValue(maxWidth[1])
        }
        return not ? !res : res
      })
      return
    }
    if (!isSupported.value)
      return

    mediaQuery.value = window!.matchMedia(toValue(query))
    matches.value = mediaQuery.value.matches
  })

  useEventListener(mediaQuery, 'change', handler, { passive: true })

  return computed(() => matches.value)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Media Query.
 *
 * @see https://vueuse.org/useMediaQuery
 * @param query
 * @param options
 */
```

- **Parameters**:
  - `query: MaybeRefOrGetter<string>`
  - `options: ConfigurableWindow & { ssrWidth?: number }`
- **Return Type**: `any`
- **Calls**:
  - `useSSRWidth (from ../useSSRWidth)`
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `watchEffect (from vue)`
  - `toValue(query).split`
  - `queryStrings.some`
  - `queryString.includes`
  - `queryString.match`
  - `Boolean`
  - `pxValue (from @vueuse/shared)`
  - `window!.matchMedia`
  - `toValue (from vue)`
  - `useEventListener (from ../useEventListener)`
  - `computed (from vue)`
- **Internal Comments**:
```
// Exit SSR support on mounted if window available (x4)
```

### `handler(event: MediaQueryListEvent): void`

<details><summary>Code</summary>

```ts
(event: MediaQueryListEvent) => {
    matches.value = event.matches
  }
```
</details>

- **Parameters**:
  - `event: MediaQueryListEvent`
- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---