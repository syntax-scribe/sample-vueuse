[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useWindowFocus/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Functions

### `useWindowFocus(options: ConfigurableWindow): ShallowRef<boolean>`

<details><summary>Code</summary>

```ts
export function useWindowFocus(options: ConfigurableWindow = {}): ShallowRef<boolean> {
  const { window = defaultWindow } = options
  if (!window)
    return shallowRef(false)

  const focused = shallowRef(window.document.hasFocus())

  const listenerOptions = { passive: true }

  useEventListener(window, 'blur', () => {
    focused.value = false
  }, listenerOptions)

  useEventListener(window, 'focus', () => {
    focused.value = true
  }, listenerOptions)

  return focused
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively track window focus with `window.onfocus` and `window.onblur`.
 *
 * @see https://vueuse.org/useWindowFocus
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `ShallowRef<boolean>`
- **Calls**:
  - `shallowRef (from vue)`
  - `window.document.hasFocus`
  - `useEventListener (from ../useEventListener)`

---