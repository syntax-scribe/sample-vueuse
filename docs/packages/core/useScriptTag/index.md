[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 3 |
| ⚡ Async/Await Patterns | 2 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useScriptTag/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `noop` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `tryOnUnmounted` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `_promise` | `Promise<HTMLScriptElement | boolean> | null` | let/var | `null` | ✗ |
| `shouldAppend` | `boolean` | let/var | `false` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{
      passive: true,
    }` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `useScriptTag` | *none* | new Promise(...) |
| promise-chain | `loadScript` | *none* | new Promise(...) |


---

## Functions

### `useScriptTag(src: MaybeRefOrGetter<string>, onLoaded: (el: HTMLScriptElement) => void, options: UseScriptTagOptions): { scriptTag: any; load: (waitForScriptLoad?: boolean) => Promise<boolean | HTMLScriptElement>; unload: () => void; }`

<details><summary>Code</summary>

```ts
export function useScriptTag(
  src: MaybeRefOrGetter<string>,
  onLoaded: (el: HTMLScriptElement) => void = noop,
  options: UseScriptTagOptions = {},
) {
  const {
    immediate = true,
    manual = false,
    type = 'text/javascript',
    async = true,
    crossOrigin,
    referrerPolicy,
    noModule,
    defer,
    document = defaultDocument,
    attrs = {},
  } = options
  const scriptTag = shallowRef<HTMLScriptElement | null>(null)

  let _promise: Promise<HTMLScriptElement | boolean> | null = null

  /**
   * Load the script specified via `src`.
   *
   * @param waitForScriptLoad Whether if the Promise should resolve once the "load" event is emitted by the <script> attribute, or right after appending it to the DOM.
   * @returns Promise<HTMLScriptElement>
   */
  const loadScript = (waitForScriptLoad: boolean): Promise<HTMLScriptElement | boolean> => new Promise((resolve, reject) => {
    // Some little closure for resolving the Promise.
    const resolveWithElement = (el: HTMLScriptElement) => {
      scriptTag.value = el
      resolve(el)
      return el
    }

    // Check if document actually exists, otherwise resolve the Promise (SSR Support).
    if (!document) {
      resolve(false)
      return
    }

    // Local variable defining if the <script> tag should be appended or not.
    let shouldAppend = false

    let el = document.querySelector<HTMLScriptElement>(`script[src="${toValue(src)}"]`)

    // Script tag not found, preparing the element for appending
    if (!el) {
      el = document.createElement('script')
      el.type = type
      el.async = async
      el.src = toValue(src)

      // Optional attributes
      if (defer)
        el.defer = defer
      if (crossOrigin)
        el.crossOrigin = crossOrigin
      if (noModule)
        el.noModule = noModule
      if (referrerPolicy)
        el.referrerPolicy = referrerPolicy

      Object.entries(attrs).forEach(([name, value]) => el?.setAttribute(name, value))

      // Enables shouldAppend
      shouldAppend = true
    }
    // Script tag already exists, resolve the loading Promise with it.
    else if (el.hasAttribute('data-loaded')) {
      resolveWithElement(el)
    }

    // Event listeners
    const listenerOptions = {
      passive: true,
    }
    useEventListener(el, 'error', event => reject(event), listenerOptions)
    useEventListener(el, 'abort', event => reject(event), listenerOptions)
    useEventListener(el, 'load', () => {
      el!.setAttribute('data-loaded', 'true')

      onLoaded(el!)
      resolveWithElement(el!)
    }, listenerOptions)

    // Append the <script> tag to head.
    if (shouldAppend)
      el = document.head.appendChild(el)

    // If script load awaiting isn't needed, we can resolve the Promise.
    if (!waitForScriptLoad)
      resolveWithElement(el)
  })

  /**
   * Exposed singleton wrapper for `loadScript`, avoiding calling it twice.
   *
   * @param waitForScriptLoad Whether if the Promise should resolve once the "load" event is emitted by the <script> attribute, or right after appending it to the DOM.
   * @returns Promise<HTMLScriptElement>
   */
  const load = (waitForScriptLoad = true): Promise<HTMLScriptElement | boolean> => {
    if (!_promise)
      _promise = loadScript(waitForScriptLoad)

    return _promise
  }

  /**
   * Unload the script specified by `src`.
   */
  const unload = () => {
    if (!document)
      return

    _promise = null

    if (scriptTag.value)
      scriptTag.value = null

    const el = document.querySelector<HTMLScriptElement>(`script[src="${toValue(src)}"]`)
    if (el)
      document.head.removeChild(el)
  }

  if (immediate && !manual)
    tryOnMounted(load)

  if (!manual)
    tryOnUnmounted(unload)

  return { scriptTag, load, unload }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Async script tag loading.
 *
 * @see https://vueuse.org/useScriptTag
 * @param src
 * @param onLoaded
 * @param options
 */
```

- **Parameters**:
  - `src: MaybeRefOrGetter<string>`
  - `onLoaded: (el: HTMLScriptElement) => void`
  - `options: UseScriptTagOptions`
- **Return Type**: `{ scriptTag: any; load: (waitForScriptLoad?: boolean) => Promise<boolean | HTMLScriptElement>; unload: () => void; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `resolve`
  - `document.querySelector`
  - `toValue (from vue)`
  - `document.createElement`
  - `Object.entries(attrs).forEach`
  - `el?.setAttribute`
  - `el.hasAttribute`
  - `resolveWithElement`
  - `useEventListener (from ../useEventListener)`
  - `reject`
  - `el!.setAttribute`
  - `onLoaded`
  - `document.head.appendChild`
  - `loadScript`
  - `document.head.removeChild`
  - `tryOnMounted (from @vueuse/shared)`
  - `tryOnUnmounted (from @vueuse/shared)`
- **Internal Comments**:
```
/**
   * Load the script specified via `src`.
   *
   * @param waitForScriptLoad Whether if the Promise should resolve once the "load" event is emitted by the <script> attribute, or right after appending it to the DOM.
   * @returns Promise<HTMLScriptElement>
   */ (x2)
// Some little closure for resolving the Promise. (x2)
// Check if document actually exists, otherwise resolve the Promise (SSR Support).
// Local variable defining if the <script> tag should be appended or not. (x2)
// Script tag not found, preparing the element for appending
// Optional attributes
// Enables shouldAppend (x3)
// Event listeners (x2)
// Append the <script> tag to head.
// If script load awaiting isn't needed, we can resolve the Promise.
/**
   * Exposed singleton wrapper for `loadScript`, avoiding calling it twice.
   *
   * @param waitForScriptLoad Whether if the Promise should resolve once the "load" event is emitted by the <script> attribute, or right after appending it to the DOM.
   * @returns Promise<HTMLScriptElement>
   */ (x2)
/**
   * Unload the script specified by `src`.
   */ (x2)
```

### `loadScript(waitForScriptLoad: boolean): Promise<HTMLScriptElement | boolean>`

<details><summary>Code</summary>

```ts
(waitForScriptLoad: boolean): Promise<HTMLScriptElement | boolean> => new Promise((resolve, reject) => {
    // Some little closure for resolving the Promise.
    const resolveWithElement = (el: HTMLScriptElement) => {
      scriptTag.value = el
      resolve(el)
      return el
    }

    // Check if document actually exists, otherwise resolve the Promise (SSR Support).
    if (!document) {
      resolve(false)
      return
    }

    // Local variable defining if the <script> tag should be appended or not.
    let shouldAppend = false

    let el = document.querySelector<HTMLScriptElement>(`script[src="${toValue(src)}"]`)

    // Script tag not found, preparing the element for appending
    if (!el) {
      el = document.createElement('script')
      el.type = type
      el.async = async
      el.src = toValue(src)

      // Optional attributes
      if (defer)
        el.defer = defer
      if (crossOrigin)
        el.crossOrigin = crossOrigin
      if (noModule)
        el.noModule = noModule
      if (referrerPolicy)
        el.referrerPolicy = referrerPolicy

      Object.entries(attrs).forEach(([name, value]) => el?.setAttribute(name, value))

      // Enables shouldAppend
      shouldAppend = true
    }
    // Script tag already exists, resolve the loading Promise with it.
    else if (el.hasAttribute('data-loaded')) {
      resolveWithElement(el)
    }

    // Event listeners
    const listenerOptions = {
      passive: true,
    }
    useEventListener(el, 'error', event => reject(event), listenerOptions)
    useEventListener(el, 'abort', event => reject(event), listenerOptions)
    useEventListener(el, 'load', () => {
      el!.setAttribute('data-loaded', 'true')

      onLoaded(el!)
      resolveWithElement(el!)
    }, listenerOptions)

    // Append the <script> tag to head.
    if (shouldAppend)
      el = document.head.appendChild(el)

    // If script load awaiting isn't needed, we can resolve the Promise.
    if (!waitForScriptLoad)
      resolveWithElement(el)
  })
```
</details>

- **Parameters**:
  - `waitForScriptLoad: boolean`
- **Return Type**: `Promise<HTMLScriptElement | boolean>`
### `resolveWithElement(el: HTMLScriptElement): HTMLScriptElement`

<details><summary>Code</summary>

```ts
(el: HTMLScriptElement) => {
      scriptTag.value = el
      resolve(el)
      return el
    }
```
</details>

- **Parameters**:
  - `el: HTMLScriptElement`
- **Return Type**: `HTMLScriptElement`
- **Calls**:
  - `resolve`
### `load(waitForScriptLoad: boolean): Promise<HTMLScriptElement | boolean>`

<details><summary>Code</summary>

```ts
(waitForScriptLoad = true): Promise<HTMLScriptElement | boolean> => {
    if (!_promise)
      _promise = loadScript(waitForScriptLoad)

    return _promise
  }
```
</details>

- **Parameters**:
  - `waitForScriptLoad: boolean`
- **Return Type**: `Promise<HTMLScriptElement | boolean>`
- **Calls**:
  - `loadScript`
### `unload(): void`

<details><summary>Code</summary>

```ts
() => {
    if (!document)
      return

    _promise = null

    if (scriptTag.value)
      scriptTag.value = null

    const el = document.querySelector<HTMLScriptElement>(`script[src="${toValue(src)}"]`)
    if (el)
      document.head.removeChild(el)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `document.querySelector`
  - `toValue (from vue)`
  - `document.head.removeChild`

---

## Interfaces

### `UseScriptTagOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseScriptTagOptions extends ConfigurableDocument {
  /**
   * Load the script immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Add `async` attribute to the script tag
   *
   * @default true
   */
  async?: boolean

  /**
   * Script type
   *
   * @default 'text/javascript'
   */
  type?: string

  /**
   * Manual controls the timing of loading and unloading
   *
   * @default false
   */
  manual?: boolean

  crossOrigin?: 'anonymous' | 'use-credentials'
  referrerPolicy?: 'no-referrer' | 'no-referrer-when-downgrade' | 'origin' | 'origin-when-cross-origin' | 'same-origin' | 'strict-origin' | 'strict-origin-when-cross-origin' | 'unsafe-url'
  noModule?: boolean

  defer?: boolean

  /**
   * Add custom attribute to the script tag
   *
   */
  attrs?: Record<string, string>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |
| `async` | `boolean` | ✓ |  |
| `type` | `string` | ✓ |  |
| `manual` | `boolean` | ✓ |  |
| `crossOrigin` | `'anonymous' | 'use-credentials'` | ✓ |  |
| `referrerPolicy` | `'no-referrer' | 'no-referrer-when-downgrade' | 'origin' | 'origin-when-cross-origin' | 'same-origin' | 'strict-origin' | 'strict-origin-when-cross-origin' | 'unsafe-url'` | ✓ |  |
| `noModule` | `boolean` | ✓ |  |
| `defer` | `boolean` | ✓ |  |
| `attrs` | `Record<string, string>` | ✓ |  |


---

## Type Aliases

### `UseScriptTagReturn`

```ts
type UseScriptTagReturn = ReturnType<typeof useScriptTag>;
```


---