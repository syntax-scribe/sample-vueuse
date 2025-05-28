[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useNavigatorLanguage/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `navigator` | `Navigator` | const | `window?.navigator` | ✗ |


---

## Functions

### `useNavigatorLanguage(options: ConfigurableWindow): Readonly<NavigatorLanguageState>`

<details><summary>Code</summary>

```ts
export function useNavigatorLanguage(options: ConfigurableWindow = {}): Readonly<NavigatorLanguageState> {
  const { window = defaultWindow } = options

  const navigator = window?.navigator

  const isSupported = useSupported(() => navigator && 'language' in navigator)

  const language = shallowRef<string | undefined>(navigator?.language)

  // Listen to when to user changes language:
  useEventListener(window, 'languagechange', () => {
    if (navigator)
      language.value = navigator.language
  }, { passive: true })

  return {
    isSupported,
    language,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 *
 * Reactive useNavigatorLanguage
 *
 * Detects the currently selected user language and returns a reactive language
 * @see https://vueuse.org/useNavigatorLanguage
 *
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `Readonly<NavigatorLanguageState>`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `useEventListener (from ../useEventListener)`
- **Internal Comments**:
```
// Listen to when to user changes language: (x3)
```


---

## Interfaces

### `NavigatorLanguageState`

<details><summary>Interface Code</summary>

```ts
export interface NavigatorLanguageState {
  isSupported: ComputedRef<boolean>
  /**
   *
   * ISO 639-1 standard Language Code
   *
   * @info The detected user agent language preference as a language tag
   * (which is sometimes referred to as a "locale identifier").
   * This consists of a 2-3 letter base language tag that indicates a
   * language, optionally followed by additional subtags separated by
   * '-'. The most common extra information is the country or region
   * variant (like 'en-US' or 'fr-CA').
   *
   *
   * @see https://www.iso.org/iso-639-language-codes.html
   * @see https://www.loc.gov/standards/iso639-2/php/code_list.php
   *
   */
  language: ShallowRef<string | undefined>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `language` | `ShallowRef<string | undefined>` | ✗ |  |


---

## Type Aliases

### `UseNavigatorLanguageReturn`

```ts
type UseNavigatorLanguageReturn = ReturnType<typeof useNavigatorLanguage>;
```


---