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
📂 **`packages/core/usePreferredReducedTransparency/index.ts`**

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

### `usePreferredReducedTransparency(options: ConfigurableWindow): any`

<details><summary>Code</summary>

```ts
export function usePreferredReducedTransparency(options?: ConfigurableWindow) {
  const isReduced = useMediaQuery('(prefers-reduced-transparency: reduce)', options)

  return computed<ReducedTransparencyType>(() => {
    if (isReduced.value)
      return 'reduce'
    return 'no-preference'
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive prefers-reduced-transparency media query.
 *
 * @see https://vueuse.org/usePreferredReducedTransparency
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

### `ReducedTransparencyType`

```ts
type ReducedTransparencyType = 'reduce' | 'no-preference';
```


---