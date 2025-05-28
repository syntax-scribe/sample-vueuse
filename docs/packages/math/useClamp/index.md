[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/math/useClamp/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ReadonlyRefOrGetter` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `clamp` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `isReadonly` | `vue` |
| `toValue` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useClamp(value: ReadonlyRefOrGetter<number>, min: MaybeRefOrGetter<number>, max: MaybeRefOrGetter<number>): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function useClamp(
  value: ReadonlyRefOrGetter<number>,
  min: MaybeRefOrGetter<number>,
  max: MaybeRefOrGetter<number>,
): ComputedRef<number>
```
</details>

- **Parameters**:
  - `value: ReadonlyRefOrGetter<number>`
  - `min: MaybeRefOrGetter<number>`
  - `max: MaybeRefOrGetter<number>`
- **Return Type**: `ComputedRef<number>`

---