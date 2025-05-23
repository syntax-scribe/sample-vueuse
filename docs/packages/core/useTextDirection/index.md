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
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


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