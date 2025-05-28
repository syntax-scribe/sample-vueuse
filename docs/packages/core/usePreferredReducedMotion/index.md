[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/usePreferredReducedMotion/index.ts`**

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

### `usePreferredReducedMotion(options: ConfigurableWindow): any`

<details><summary>Code</summary>

```ts
export function usePreferredReducedMotion(options?: ConfigurableWindow) {
  const isReduced = useMediaQuery('(prefers-reduced-motion: reduce)', options)

  return computed<ReducedMotionType>(() => {
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
 * Reactive prefers-reduced-motion media query.
 *
 * @see https://vueuse.org/usePreferredReducedMotion
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

### `ReducedMotionType`

```ts
type ReducedMotionType = 'reduce' | 'no-preference';
```


---