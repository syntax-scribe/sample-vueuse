[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/usePreferredColorScheme/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `computed` | `vue` |
| `useMediaQuery` | `../useMediaQuery` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `usePreferredColorScheme(options: ConfigurableWindow): any`

<details><summary>Code</summary>

```ts
export function usePreferredColorScheme(options?: ConfigurableWindow) {
  const isLight = useMediaQuery('(prefers-color-scheme: light)', options)
  const isDark = useMediaQuery('(prefers-color-scheme: dark)', options)

  return computed<ColorSchemeType>(() => {
    if (isDark.value)
      return 'dark'
    if (isLight.value)
      return 'light'
    return 'no-preference'
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive prefers-color-scheme media query.
 *
 * @see https://vueuse.org/usePreferredColorScheme
 * @param [options]
 */
```

- **Parameters**:
  - `options: ConfigurableWindow`
- **Return Type**: `any`
- **Calls**:
  - `useMediaQuery (from ../useMediaQuery)`
  - `computed (from vue)`

---

## Type Aliases

### `ColorSchemeType`

```ts
type ColorSchemeType = 'dark' | 'light' | 'no-preference';
```


---