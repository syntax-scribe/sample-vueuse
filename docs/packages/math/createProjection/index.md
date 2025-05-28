[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/math/createProjection/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ProjectorFunction` | `../createGenericProjection` |
| `UseProjection` | `../createGenericProjection` |
| `createGenericProjection` | `../createGenericProjection` |


---

## Functions

### `defaultNumericProjector(input: number, from: readonly [number, number], to: readonly [number, number]): number`

<details><summary>Code</summary>

```ts
function defaultNumericProjector(input: number, from: readonly [number, number], to: readonly [number, number]) {
  return (input - from[0]) / (from[1] - from[0]) * (to[1] - to[0]) + to[0]
}
```
</details>

- **Parameters**:
  - `input: number`
  - `from: readonly [number, number]`
  - `to: readonly [number, number]`
- **Return Type**: `number`
### `createProjection(fromDomain: MaybeRefOrGetter<readonly [number, number]>, toDomain: MaybeRefOrGetter<readonly [number, number]>, projector: ProjectorFunction<number, number>): UseProjection<number, number>`

<details><summary>Code</summary>

```ts
export function createProjection(
  fromDomain: MaybeRefOrGetter<readonly [number, number]>,
  toDomain: MaybeRefOrGetter<readonly [number, number]>,
  projector: ProjectorFunction<number, number> = defaultNumericProjector,
): UseProjection<number, number> {
  return createGenericProjection(fromDomain, toDomain, projector)
}
```
</details>

- **Parameters**:
  - `fromDomain: MaybeRefOrGetter<readonly [number, number]>`
  - `toDomain: MaybeRefOrGetter<readonly [number, number]>`
  - `projector: ProjectorFunction<number, number>`
- **Return Type**: `UseProjection<number, number>`
- **Calls**:
  - `createGenericProjection (from ../createGenericProjection)`

---