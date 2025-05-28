[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `WRITABLE_PROPERTIES` | `readonly ["hash", "host", "hostname", "href", "pathname", "port", "protocol", "search"]` | const | `[
  'hash',
  'host',
  'hostname',
  'href',
  'pathname',
  'port',
  'protocol',
  'search',
] as const` | ✗ |
| `refs` | `Record<"search" | "hash" | "host" | "hostname" | "href" | "pathname" | "port" | "protocol", Ref<string>>` | const | `Object.fromEntries(
    WRITABLE_PROPERTIES.map(key => [key, deepRef()]),
  ) as Record<typeof WRITABLE_PROPERTIES[number], Ref<string | undefined>>` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


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