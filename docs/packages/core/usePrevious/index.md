[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 6 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/usePrevious/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `toRef` | `@vueuse/shared` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `usePrevious(value: MaybeRefOrGetter<T>): Readonly<ShallowRef<T | undefined>>`

<details><summary>Code</summary>

```ts
export function usePrevious<T>(value: MaybeRefOrGetter<T>): Readonly<ShallowRef<T | undefined>>
```
</details>

- **JSDoc**:
```ts
/**
 * Holds the previous value of a ref.
 *
 * @see   {@link https://vueuse.org/usePrevious}
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<T>`
- **Return Type**: `Readonly<ShallowRef<T | undefined>>`

---