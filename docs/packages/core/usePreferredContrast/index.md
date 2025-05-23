[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/usePreferredContrast/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `computed` | `vue` |
| `useMediaQuery` | `../useMediaQuery` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `ContrastType`

```ts
type ContrastType = 'more' | 'less' | 'custom' | 'no-preference';
```


---