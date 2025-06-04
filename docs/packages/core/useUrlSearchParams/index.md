[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 7 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 6 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useUrlSearchParams/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `pausableWatch` | `@vueuse/shared` |
| `reactive` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `hash` | `string` | const | `window.location.hash || ''` | ✗ |
| `hash` | `string` | const | `window.location.hash || '#'` | ✗ |
| `unusedKeys` | `Set<string>` | const | `new Set(Object.keys(state))` | ✗ |
| `params` | `URLSearchParams` | const | `new URLSearchParams('')` | ✗ |
| `mapEntry` | `any` | const | `state[key]` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


---

## Functions

### `useUrlSearchParams(mode: 'history' | 'hash' | 'hash-params', options: UseUrlSearchParamsOptions<T>): T`

<details><summary>Code</summary>

```ts
export function useUrlSearchParams<T extends Record<string, any> = UrlParams>(
  mode: 'history' | 'hash' | 'hash-params' = 'history',
  options: UseUrlSearchParamsOptions<T> = {},
): T {
  const {
    initialValue = {},
    removeNullishValues = true,
    removeFalsyValues = false,
    write: enableWrite = true,
    writeMode = 'replace',
    window = defaultWindow!,
  } = options

  if (!window)
    return reactive(initialValue) as T

  const state: Record<string, any> = reactive({})

  function getRawParams() {
    if (mode === 'history') {
      return window.location.search || ''
    }
    else if (mode === 'hash') {
      const hash = window.location.hash || ''
      const index = hash.indexOf('?')
      return index > 0 ? hash.slice(index) : ''
    }
    else {
      return (window.location.hash || '').replace(/^#/, '')
    }
  }

  function constructQuery(params: URLSearchParams) {
    const stringified = params.toString()

    if (mode === 'history')
      return `${stringified ? `?${stringified}` : ''}${window.location.hash || ''}`
    if (mode === 'hash-params')
      return `${window.location.search || ''}${stringified ? `#${stringified}` : ''}`
    const hash = window.location.hash || '#'
    const index = hash.indexOf('?')
    if (index > 0)
      return `${window.location.search || ''}${hash.slice(0, index)}${stringified ? `?${stringified}` : ''}`
    return `${window.location.search || ''}${hash}${stringified ? `?${stringified}` : ''}`
  }

  function read() {
    return new URLSearchParams(getRawParams())
  }

  function updateState(params: URLSearchParams) {
    const unusedKeys = new Set(Object.keys(state))
    for (const key of params.keys()) {
      const paramsForKey = params.getAll(key)
      state[key] = paramsForKey.length > 1
        ? paramsForKey
        : (params.get(key) || '')
      unusedKeys.delete(key)
    }
    Array.from(unusedKeys).forEach(key => delete state[key])
  }

  const { pause, resume } = pausableWatch(
    state,
    () => {
      const params = new URLSearchParams('')
      Object.keys(state).forEach((key) => {
        const mapEntry = state[key]
        if (Array.isArray(mapEntry))
          mapEntry.forEach(value => params.append(key, value))
        else if (removeNullishValues && mapEntry == null)
          params.delete(key)
        else if (removeFalsyValues && !mapEntry)
          params.delete(key)
        else
          params.set(key, mapEntry)
      })
      write(params, false)
    },
    { deep: true },
  )

  function write(params: URLSearchParams, shouldUpdate: boolean) {
    pause()

    if (shouldUpdate)
      updateState(params)

    if (writeMode === 'replace') {
      window.history.replaceState(
        window.history.state,
        window.document.title,
        window.location.pathname + constructQuery(params),
      )
    }
    else {
      window.history.pushState(
        window.history.state,
        window.document.title,
        window.location.pathname + constructQuery(params),
      )
    }

    resume()
  }

  function onChanged() {
    if (!enableWrite)
      return

    write(read(), true)
  }

  const listenerOptions = { passive: true }

  useEventListener(window, 'popstate', onChanged, listenerOptions)
  if (mode !== 'history')
    useEventListener(window, 'hashchange', onChanged, listenerOptions)

  const initial = read()
  if (initial.keys().next().value)
    updateState(initial)
  else
    Object.assign(state, initialValue)

  return state as T
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive URLSearchParams
 *
 * @see https://vueuse.org/useUrlSearchParams
 * @param mode
 * @param options
 */
```

- **Parameters**:
  - `mode: 'history' | 'hash' | 'hash-params'`
  - `options: UseUrlSearchParamsOptions<T>`
- **Return Type**: `T`
- **Calls**:
  - `reactive (from vue)`
  - `hash.indexOf`
  - `hash.slice`
  - `(window.location.hash || '').replace`
  - `params.toString`
  - `getRawParams`
  - `Object.keys`
  - `params.keys`
  - `params.getAll`
  - `params.get`
  - `unusedKeys.delete`
  - `Array.from(unusedKeys).forEach`
  - `pausableWatch (from @vueuse/shared)`
  - `Object.keys(state).forEach`
  - `Array.isArray`
  - `mapEntry.forEach`
  - `params.append`
  - `params.delete`
  - `params.set`
  - `write`
  - `pause`
  - `updateState`
  - `window.history.replaceState`
  - `constructQuery`
  - `window.history.pushState`
  - `resume`
  - `read`
  - `useEventListener (from ../useEventListener)`
  - `initial.keys().next`
  - `Object.assign`
### `getRawParams(): string`

<details><summary>Code</summary>

```ts
function getRawParams() {
    if (mode === 'history') {
      return window.location.search || ''
    }
    else if (mode === 'hash') {
      const hash = window.location.hash || ''
      const index = hash.indexOf('?')
      return index > 0 ? hash.slice(index) : ''
    }
    else {
      return (window.location.hash || '').replace(/^#/, '')
    }
  }
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `hash.indexOf`
  - `hash.slice`
  - `(window.location.hash || '').replace`
### `constructQuery(params: URLSearchParams): string`

<details><summary>Code</summary>

```ts
function constructQuery(params: URLSearchParams) {
    const stringified = params.toString()

    if (mode === 'history')
      return `${stringified ? `?${stringified}` : ''}${window.location.hash || ''}`
    if (mode === 'hash-params')
      return `${window.location.search || ''}${stringified ? `#${stringified}` : ''}`
    const hash = window.location.hash || '#'
    const index = hash.indexOf('?')
    if (index > 0)
      return `${window.location.search || ''}${hash.slice(0, index)}${stringified ? `?${stringified}` : ''}`
    return `${window.location.search || ''}${hash}${stringified ? `?${stringified}` : ''}`
  }
```
</details>

- **Parameters**:
  - `params: URLSearchParams`
- **Return Type**: `string`
- **Calls**:
  - `params.toString`
  - `hash.indexOf`
  - `hash.slice`
### `read(): URLSearchParams`

<details><summary>Code</summary>

```ts
function read() {
    return new URLSearchParams(getRawParams())
  }
```
</details>

- **Return Type**: `URLSearchParams`
- **Calls**:
  - `getRawParams`
### `updateState(params: URLSearchParams): void`

<details><summary>Code</summary>

```ts
function updateState(params: URLSearchParams) {
    const unusedKeys = new Set(Object.keys(state))
    for (const key of params.keys()) {
      const paramsForKey = params.getAll(key)
      state[key] = paramsForKey.length > 1
        ? paramsForKey
        : (params.get(key) || '')
      unusedKeys.delete(key)
    }
    Array.from(unusedKeys).forEach(key => delete state[key])
  }
```
</details>

- **Parameters**:
  - `params: URLSearchParams`
- **Return Type**: `void`
- **Calls**:
  - `Object.keys`
  - `params.keys`
  - `params.getAll`
  - `params.get`
  - `unusedKeys.delete`
  - `Array.from(unusedKeys).forEach`
### `write(params: URLSearchParams, shouldUpdate: boolean): void`

<details><summary>Code</summary>

```ts
function write(params: URLSearchParams, shouldUpdate: boolean) {
    pause()

    if (shouldUpdate)
      updateState(params)

    if (writeMode === 'replace') {
      window.history.replaceState(
        window.history.state,
        window.document.title,
        window.location.pathname + constructQuery(params),
      )
    }
    else {
      window.history.pushState(
        window.history.state,
        window.document.title,
        window.location.pathname + constructQuery(params),
      )
    }

    resume()
  }
```
</details>

- **Parameters**:
  - `params: URLSearchParams`
  - `shouldUpdate: boolean`
- **Return Type**: `void`
- **Calls**:
  - `pause`
  - `updateState`
  - `window.history.replaceState`
  - `constructQuery`
  - `window.history.pushState`
  - `resume`
### `onChanged(): void`

<details><summary>Code</summary>

```ts
function onChanged() {
    if (!enableWrite)
      return

    write(read(), true)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `write`
  - `read`

---

## Interfaces

### `UseUrlSearchParamsOptions<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseUrlSearchParamsOptions<T> extends ConfigurableWindow {
  /**
   * @default true
   */
  removeNullishValues?: boolean

  /**
   * @default false
   */
  removeFalsyValues?: boolean

  /**
   * @default {}
   */
  initialValue?: T

  /**
   * Write back to `window.history` automatically
   *
   * @default true
   */
  write?: boolean

  /**
   * Write mode for `window.history` when `write` is enabled
   * - `replace`: replace the current history entry
   * - `push`: push a new history entry
   * @default 'replace'
   */
  writeMode?: 'replace' | 'push'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `removeNullishValues` | `boolean` | ✓ |  |
| `removeFalsyValues` | `boolean` | ✓ |  |
| `initialValue` | `T` | ✓ |  |
| `write` | `boolean` | ✓ |  |
| `writeMode` | `'replace' | 'push'` | ✓ |  |


---

## Type Aliases

### `UrlParams`

```ts
type UrlParams = Record<string, string[] | string>;
```


---