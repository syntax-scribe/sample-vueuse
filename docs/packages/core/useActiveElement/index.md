[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `document` | `DocumentOrShadowRoot` | const | `options.document ?? window?.document` | ✗ |
| `element` | `Element` | let/var | `document?.activeElement` | ✗ |
| `listenerOptions` | `{ capture: boolean; passive: boolean; }` | const | `{
      capture: true,
      passive: true,
    }` | ✗ |


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