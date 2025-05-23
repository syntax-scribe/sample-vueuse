[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---