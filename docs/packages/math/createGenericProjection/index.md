[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 2

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


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