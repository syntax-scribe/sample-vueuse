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
- **Imports**: 8
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useBrowserLocation/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `objectEntries` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `reactive` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useBrowserLocation(options: ConfigurableWindow): any`

<details><summary>Code</summary>

```ts
export function useBrowserLocation(options: ConfigurableWindow = {}) {
  const { window = defaultWindow } = options
  const refs = Object.fromEntries(
    WRITABLE_PROPERTIES.map(key => [key, deepRef()]),
  ) as Record<typeof WRITABLE_PROPERTIES[number], Ref<string | undefined>>

  for (const [key, ref] of objectEntries(refs)) {
    watch(ref, (value) => {
      if (!window?.location || window.location[key] === value)
        return
      window.location[key] = value!
    })
  }

  const buildState = (trigger: string): BrowserLocationState => {
    const { state, length } = window?.history || {}
    const { origin } = window?.location || {}

    for (const key of WRITABLE_PROPERTIES)
      refs[key].value = window?.location?.[key]

    return reactive({
      trigger,
      state,
      length,
      origin,
      ...refs,
    })
  }

  const state = deepRef(buildState('load'))

  if (window) {
    const listenerOptions = { passive: true }
    useEventListener(window, 'popstate', () => state.value = buildState('popstate'), listenerOptions)
    useEventListener(window, 'hashchange', () => state.value = buildState('hashchange'), listenerOptions)
  }

  return state
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive browser location.
 *
 * @see https://vueuse.org/useBrowserLocation
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `any`
- **Calls**:
  - `Object.fromEntries`
  - `WRITABLE_PROPERTIES.map`
  - `deepRef (from vue)`
  - `objectEntries (from @vueuse/shared)`
  - `watch (from vue)`
  - `reactive (from vue)`
  - `buildState`
  - `useEventListener (from ../useEventListener)`
### `buildState(trigger: string): BrowserLocationState`

<details><summary>Code</summary>

```ts
(trigger: string): BrowserLocationState => {
    const { state, length } = window?.history || {}
    const { origin } = window?.location || {}

    for (const key of WRITABLE_PROPERTIES)
      refs[key].value = window?.location?.[key]

    return reactive({
      trigger,
      state,
      length,
      origin,
      ...refs,
    })
  }
```
</details>

- **Parameters**:
  - `trigger: string`
- **Return Type**: `BrowserLocationState`
- **Calls**:
  - `reactive (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `BrowserLocationState`

<details><summary>Interface Code</summary>

```ts
export interface BrowserLocationState {
  readonly trigger: string
  readonly state?: any
  readonly length?: number
  readonly origin?: string
  hash?: string
  host?: string
  hostname?: string
  href?: string
  pathname?: string
  port?: string
  protocol?: string
  search?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `trigger` | `string` | ✗ |  |
| `state` | `any` | ✓ |  |
| `length` | `number` | ✓ |  |
| `origin` | `string` | ✓ |  |
| `hash` | `string` | ✓ |  |
| `host` | `string` | ✓ |  |
| `hostname` | `string` | ✓ |  |
| `href` | `string` | ✓ |  |
| `pathname` | `string` | ✓ |  |
| `port` | `string` | ✓ |  |
| `protocol` | `string` | ✓ |  |
| `search` | `string` | ✓ |  |


---

## Type Aliases

### `UseBrowserLocationReturn`

```ts
type UseBrowserLocationReturn = ReturnType<typeof useBrowserLocation>;
```


---