[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

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