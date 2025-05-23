[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/math/useProjection/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ProjectorFunction` | `../createGenericProjection` |
| `createProjection` | `../createProjection` |


---

## Functions

### `useProjection(input: MaybeRefOrGetter<number>, fromDomain: MaybeRefOrGetter<readonly [number, number]>, toDomain: MaybeRefOrGetter<readonly [number, number]>, projector: ProjectorFunction<number, number>): ComputedRef<T>`

<details><summary>Code</summary>

```ts
export function useProjection(
  input: MaybeRefOrGetter<number>,
  fromDomain: MaybeRefOrGetter<readonly [number, number]>,
  toDomain: MaybeRefOrGetter<readonly [number, number]>,
  projector?: ProjectorFunction<number, number>,
) {
  return createProjection(fromDomain, toDomain, projector)(input)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive numeric projection from one domain to another.
 *
 * @see https://vueuse.org/useProjection
 */
```

- **Parameters**:
  - `input: MaybeRefOrGetter<number>`
  - `fromDomain: MaybeRefOrGetter<readonly [number, number]>`
  - `toDomain: MaybeRefOrGetter<readonly [number, number]>`
  - `projector: ProjectorFunction<number, number>`
- **Return Type**: `ComputedRef<T>`
- **Calls**:
  - `complex_call_523`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---