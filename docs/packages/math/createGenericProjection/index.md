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
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/math/createGenericProjection/index.ts`**

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

### `createGenericProjection(fromDomain: MaybeRefOrGetter<readonly [F, F]>, toDomain: MaybeRefOrGetter<readonly [T, T]>, projector: ProjectorFunction<F, T>): UseProjection<F, T>`

<details><summary>Code</summary>

```ts
export function createGenericProjection<F = number, T = number>(
  fromDomain: MaybeRefOrGetter<readonly [F, F]>,
  toDomain: MaybeRefOrGetter<readonly [T, T]>,
  projector: ProjectorFunction<F, T>,
): UseProjection<F, T> {
  return (input: MaybeRefOrGetter<F>) => {
    return computed(() => projector(toValue(input), toValue(fromDomain), toValue(toDomain)))
  }
}
```
</details>

- **Parameters**:
  - `fromDomain: MaybeRefOrGetter<readonly [F, F]>`
  - `toDomain: MaybeRefOrGetter<readonly [T, T]>`
  - `projector: ProjectorFunction<F, T>`
- **Return Type**: `UseProjection<F, T>`
- **Calls**:
  - `computed (from vue)`
  - `projector`
  - `toValue (from vue)`

---

## Type Aliases

### `ProjectorFunction<F, T>`

```ts
type ProjectorFunction<F, T> = (input: F, from: readonly [F, F], to: readonly [T, T]) => T;
```

### `UseProjection<F, T>`

```ts
type UseProjection<F, T> = (input: MaybeRefOrGetter<F>) => ComputedRef<T>;
```


---