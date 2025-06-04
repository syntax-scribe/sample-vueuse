[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useStyleTag/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `tryOnMounted` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `defaultDocument` | `../_configurable` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `_id` | `number` | let/var | `0` | ✗ |
| `el` | `HTMLStyleElement` | const | `(document.getElementById(id) || document.createElement('style')) as HTMLStyleElement` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useStyleTag(css: MaybeRef<string>, options: UseStyleTagOptions): UseStyleTagReturn`

<details><summary>Code</summary>

```ts
export function useStyleTag(
  css: MaybeRef<string>,
  options: UseStyleTagOptions = {},
): UseStyleTagReturn {
  const isLoaded = shallowRef(false)

  const {
    document = defaultDocument,
    immediate = true,
    manual = false,
    id = `vueuse_styletag_${++_id}`,
  } = options

  const cssRef = shallowRef(css)

  let stop = () => { }
  const load = () => {
    if (!document)
      return

    const el = (document.getElementById(id) || document.createElement('style')) as HTMLStyleElement

    if (!el.isConnected) {
      el.id = id
      if (options.nonce)
        el.nonce = options.nonce
      if (options.media)
        el.media = options.media
      document.head.appendChild(el)
    }

    if (isLoaded.value)
      return

    stop = watch(
      cssRef,
      (value) => {
        el.textContent = value
      },
      { immediate: true },
    )

    isLoaded.value = true
  }

  const unload = () => {
    if (!document || !isLoaded.value)
      return
    stop()
    document.head.removeChild(document.getElementById(id) as HTMLStyleElement)
    isLoaded.value = false
  }

  if (immediate && !manual)
    tryOnMounted(load)

  if (!manual)
    tryOnScopeDispose(unload)

  return {
    id,
    css: cssRef,
    unload,
    load,
    isLoaded: readonly(isLoaded),
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Inject <style> element in head.
 *
 * Overload: Omitted id
 *
 * @see https://vueuse.org/useStyleTag
 * @param css
 * @param options
 */
```

- **Parameters**:
  - `css: MaybeRef<string>`
  - `options: UseStyleTagOptions`
- **Return Type**: `UseStyleTagReturn`
- **Calls**:
  - `shallowRef (from vue)`
  - `document.getElementById`
  - `document.createElement`
  - `document.head.appendChild`
  - `watch (from vue)`
  - `stop`
  - `document.head.removeChild`
  - `tryOnMounted (from @vueuse/shared)`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `readonly (from vue)`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => { }
```
</details>

- **Return Type**: `void`
### `load(): void`

<details><summary>Code</summary>

```ts
() => {
    if (!document)
      return

    const el = (document.getElementById(id) || document.createElement('style')) as HTMLStyleElement

    if (!el.isConnected) {
      el.id = id
      if (options.nonce)
        el.nonce = options.nonce
      if (options.media)
        el.media = options.media
      document.head.appendChild(el)
    }

    if (isLoaded.value)
      return

    stop = watch(
      cssRef,
      (value) => {
        el.textContent = value
      },
      { immediate: true },
    )

    isLoaded.value = true
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `document.getElementById`
  - `document.createElement`
  - `document.head.appendChild`
  - `watch (from vue)`
### `unload(): void`

<details><summary>Code</summary>

```ts
() => {
    if (!document || !isLoaded.value)
      return
    stop()
    document.head.removeChild(document.getElementById(id) as HTMLStyleElement)
    isLoaded.value = false
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stop`
  - `document.head.removeChild`
  - `document.getElementById`

---

## Interfaces

### `UseStyleTagOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseStyleTagOptions extends ConfigurableDocument {
  /**
   * Media query for styles to apply
   */
  media?: string

  /**
   * Load the style immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Manual controls the timing of loading and unloading
   *
   * @default false
   */
  manual?: boolean

  /**
   * DOM id of the style tag
   *
   * @default auto-incremented
   */
  id?: string

  /**
   * Nonce value for CSP (Content Security Policy)
   *
   * @default undefined
   */
  nonce?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `media` | `string` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `manual` | `boolean` | ✓ |  |
| `id` | `string` | ✓ |  |
| `nonce` | `string` | ✓ |  |

### `UseStyleTagReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseStyleTagReturn {
  id: string
  css: ShallowRef<string>
  load: () => void
  unload: () => void
  isLoaded: Readonly<ShallowRef<boolean>>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `id` | `string` | ✗ |  |
| `css` | `ShallowRef<string>` | ✗ |  |
| `load` | `() => void` | ✗ |  |
| `unload` | `() => void` | ✗ |  |
| `isLoaded` | `Readonly<ShallowRef<boolean>>` | ✗ |  |


---