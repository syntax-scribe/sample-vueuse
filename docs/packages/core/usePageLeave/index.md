[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/usePageLeave/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `from` | `any` | const | `event.relatedTarget || event.toElement` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Functions

### `usePageLeave(options: ConfigurableWindow): any`

<details><summary>Code</summary>

```ts
export function usePageLeave(options: ConfigurableWindow = {}) {
  const { window = defaultWindow } = options
  const isLeft = shallowRef(false)

  const handler = (event: MouseEvent) => {
    if (!window)
      return

    event = event || (window.event as any)
    // @ts-expect-error missing types
    const from = event.relatedTarget || event.toElement
    isLeft.value = !from
  }

  if (window) {
    const listenerOptions = { passive: true }
    useEventListener(window, 'mouseout', handler, listenerOptions)
    useEventListener(window.document, 'mouseleave', handler, listenerOptions)
    useEventListener(window.document, 'mouseenter', handler, listenerOptions)
  }

  return isLeft
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive state to show whether mouse leaves the page.
 *
 * @see https://vueuse.org/usePageLeave
 * @param options
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `useEventListener (from ../useEventListener)`
- **Internal Comments**:
```
// @ts-expect-error missing types (x2)
```

### `handler(event: MouseEvent): void`

<details><summary>Code</summary>

```ts
(event: MouseEvent) => {
    if (!window)
      return

    event = event || (window.event as any)
    // @ts-expect-error missing types
    const from = event.relatedTarget || event.toElement
    isLeft.value = !from
  }
```
</details>

- **Parameters**:
  - `event: MouseEvent`
- **Return Type**: `void`
- **Internal Comments**:
```
// @ts-expect-error missing types (x2)
```


---