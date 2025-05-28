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
📂 **`packages/core/usePreferredLanguages/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `deepRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `navigator` | `Navigator` | const | `window.navigator` | ✗ |


---

## Functions

### `usePreferredLanguages(options: ConfigurableWindow): Ref<readonly string[]>`

<details><summary>Code</summary>

```ts
export function usePreferredLanguages(options: ConfigurableWindow = {}): Ref<readonly string[]> {
  const { window = defaultWindow } = options
  if (!window)
    return deepRef(['en'])

  const navigator = window.navigator
  const value = deepRef<readonly string[]>(navigator.languages)

  useEventListener(window, 'languagechange', () => {
    value.value = navigator.languages
  }, { passive: true })

  return value
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Navigator Languages.
 *
 * @see https://vueuse.org/usePreferredLanguages
 * @param options
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `Ref<readonly string[]>`
- **Calls**:
  - `deepRef (from vue)`
  - `useEventListener (from ../useEventListener)`

---