[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/refDefault/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `computed` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `refDefault(source: Ref<T | undefined | null>, defaultValue: T): Ref<T>`

<details><summary>Code</summary>

```ts
export function refDefault<T>(source: Ref<T | undefined | null>, defaultValue: T): Ref<T> {
  return computed({
    get() {
      return source.value ?? defaultValue
    },
    set(value) {
      source.value = value
    },
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Apply default value to a ref.
 */
```

- **Parameters**:
  - `source: Ref<T | undefined | null>`
  - `defaultValue: T`
- **Return Type**: `Ref<T>`
- **Calls**:
  - `computed (from vue)`

---