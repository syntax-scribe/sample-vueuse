[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useActiveElement/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableDocumentOrShadowRoot` | `../_configurable` |
| `ConfigurableWindow` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `onElementRemoval` | `../onElementRemoval` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useActiveElement(options: UseActiveElementOptions): any`

<details><summary>Code</summary>

```ts
export function useActiveElement<T extends HTMLElement>(
  options: UseActiveElementOptions = {},
) {
  const {
    window = defaultWindow,
    deep = true,
    triggerOnRemoval = false,
  } = options
  const document = options.document ?? window?.document

  const getDeepActiveElement = () => {
    let element = document?.activeElement
    if (deep) {
      while (element?.shadowRoot)
        element = element?.shadowRoot?.activeElement
    }
    return element
  }

  const activeElement = shallowRef<T | null | undefined>()
  const trigger = () => {
    activeElement.value = getDeepActiveElement() as T | null | undefined
  }

  if (window) {
    const listenerOptions = {
      capture: true,
      passive: true,
    }

    useEventListener(
      window,
      'blur',
      (event) => {
        if (event.relatedTarget !== null)
          return
        trigger()
      },
      listenerOptions,
    )
    useEventListener(
      window,
      'focus',
      trigger,
      listenerOptions,
    )
  }

  if (triggerOnRemoval) {
    onElementRemoval(activeElement, trigger, { document })
  }

  trigger()

  return activeElement
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `document.activeElement`
 *
 * @see https://vueuse.org/useActiveElement
 * @param options
 */
```

- **Parameters**:
  - `options: UseActiveElementOptions`
- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `getDeepActiveElement`
  - `useEventListener (from ../useEventListener)`
  - `trigger`
  - `onElementRemoval (from ../onElementRemoval)`
### `getDeepActiveElement(): Element`

<details><summary>Code</summary>

```ts
() => {
    let element = document?.activeElement
    if (deep) {
      while (element?.shadowRoot)
        element = element?.shadowRoot?.activeElement
    }
    return element
  }
```
</details>

- **Return Type**: `Element`
### `trigger(): void`

<details><summary>Code</summary>

```ts
() => {
    activeElement.value = getDeepActiveElement() as T | null | undefined
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `getDeepActiveElement`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseActiveElementOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseActiveElementOptions extends ConfigurableWindow, ConfigurableDocumentOrShadowRoot {
  /**
   * Search active element deeply inside shadow dom
   *
   * @default true
   */
  deep?: boolean
  /**
   * Track active element when it's removed from the DOM
   * Using a MutationObserver under the hood
   * @default false
   */
  triggerOnRemoval?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `deep` | `boolean` | ✓ |  |
| `triggerOnRemoval` | `boolean` | ✓ |  |


---

## Type Aliases

> No type aliases found in this file.


---