[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/math/useTrunc/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useTrunc(value: MaybeRefOrGetter<number>): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function useTrunc(value: MaybeRefOrGetter<number>): ComputedRef<number> {
  return computed<number>(() => Math.trunc(toValue(value)))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Math.trunc`.
 *
 * @see https://vueuse.org/useTrunc
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<number>`
- **Return Type**: `ComputedRef<number>`
- **Calls**:
  - `computed (from vue)`
  - `Math.trunc`
  - `toValue (from vue)`

---