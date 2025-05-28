[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useTextDirection/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableDocument` | `../_configurable` |
| `MaybeElement` | `../unrefElement` |
| `tryOnMounted` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useMutationObserver` | `../useMutationObserver` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useTextDirection(options: UseTextDirectionOptions): any`

<details><summary>Code</summary>

```ts
export function useTextDirection(options: UseTextDirectionOptions = {}) {
  const {
    document = defaultDocument,
    selector = 'html',
    observe = false,
    initialValue = 'ltr',
  } = options

  function getValue() {
    return document?.querySelector(selector)?.getAttribute('dir') as UseTextDirectionValue ?? initialValue
  }

  const dir = deepRef<UseTextDirectionValue>(getValue())

  tryOnMounted(() => dir.value = getValue())

  if (observe && document) {
    useMutationObserver(
      document.querySelector(selector) as MaybeElement,
      () => dir.value = getValue(),
      { attributes: true },
    )
  }

  return computed<UseTextDirectionValue>({
    get() {
      return dir.value
    },
    set(v) {
      dir.value = v
      if (!document)
        return
      if (dir.value)
        document.querySelector(selector)?.setAttribute('dir', dir.value)
      else
        document.querySelector(selector)?.removeAttribute('dir')
    },
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive dir of the element's text.
 *
 * @see https://vueuse.org/useTextDirection
 */
```

- **Parameters**:
  - `options: UseTextDirectionOptions`
- **Return Type**: `any`
- **Calls**:
  - `document?.querySelector(selector)?.getAttribute`
  - `deepRef (from vue)`
  - `getValue`
  - `tryOnMounted (from @vueuse/shared)`
  - `useMutationObserver (from ../useMutationObserver)`
  - `document.querySelector`
  - `computed (from vue)`
  - `document.querySelector(selector)?.setAttribute`
  - `document.querySelector(selector)?.removeAttribute`
### `getValue(): UseTextDirectionValue`

<details><summary>Code</summary>

```ts
function getValue() {
    return document?.querySelector(selector)?.getAttribute('dir') as UseTextDirectionValue ?? initialValue
  }
```
</details>

- **Return Type**: `UseTextDirectionValue`
- **Calls**:
  - `document?.querySelector(selector)?.getAttribute`

---

## Interfaces

### `UseTextDirectionOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseTextDirectionOptions extends ConfigurableDocument {
  /**
   * CSS Selector for the target element applying to
   *
   * @default 'html'
   */
  selector?: string
  /**
   * Observe `document.querySelector(selector)` changes using MutationObserve
   *
   * @default false
   */
  observe?: boolean
  /**
   * Initial value
   *
   * @default 'ltr'
   */
  initialValue?: UseTextDirectionValue
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `selector` | `string` | ✓ |  |
| `observe` | `boolean` | ✓ |  |
| `initialValue` | `UseTextDirectionValue` | ✓ |  |


---

## Type Aliases

### `UseTextDirectionValue`

```ts
type UseTextDirectionValue = 'ltr' | 'rtl' | 'auto';
```


---