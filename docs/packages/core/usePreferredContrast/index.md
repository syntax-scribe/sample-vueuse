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
📂 **`packages/core/usePreferredContrast/index.ts`**

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

### `usePreferredContrast(options: ConfigurableWindow): any`

<details><summary>Code</summary>

```ts
export function usePreferredContrast(options?: ConfigurableWindow) {
  const isMore = useMediaQuery('(prefers-contrast: more)', options)
  const isLess = useMediaQuery('(prefers-contrast: less)', options)
  const isCustom = useMediaQuery('(prefers-contrast: custom)', options)

  return computed<ContrastType>(() => {
    if (isMore.value)
      return 'more'
    if (isLess.value)
      return 'less'
    if (isCustom.value)
      return 'custom'
    return 'no-preference'
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive prefers-contrast media query.
 *
 * @see https://vueuse.org/usePreferredContrast
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

### `ContrastType`

```ts
type ContrastType = 'more' | 'less' | 'custom' | 'no-preference';
```


---