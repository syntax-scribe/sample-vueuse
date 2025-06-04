[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/reactiveComputed/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedGetter` | `vue` |
| `UnwrapNestedRefs` | `vue` |
| `computed` | `vue` |
| `toReactive` | `../toReactive` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `reactiveComputed(fn: ComputedGetter<T>): ReactiveComputedReturn<T>`

<details><summary>Code</summary>

```ts
export function reactiveComputed<T extends object>(fn: ComputedGetter<T>): ReactiveComputedReturn<T> {
  return toReactive<T>(computed<T>(fn))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Computed reactive object.
 */
```

- **Parameters**:
  - `fn: ComputedGetter<T>`
- **Return Type**: `ReactiveComputedReturn<T>`
- **Calls**:
  - `toReactive (from ../toReactive)`
  - `computed (from vue)`

---

## Type Aliases

### `ReactiveComputedReturn<T extends object extends object>`

```ts
type ReactiveComputedReturn<T extends object extends object> = UnwrapNestedRefs<T>;
```


---