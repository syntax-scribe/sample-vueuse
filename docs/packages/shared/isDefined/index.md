[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/isDefined/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `Ref` | `vue` |
| `unref` | `vue` |


---

## Functions

### `isDefined(v: ComputedRef<T>): v is ComputedRef<Exclude<T, null | undefined>>`

<details><summary>Code</summary>

```ts
export function isDefined<T>(v: ComputedRef<T>): v is ComputedRef<Exclude<T, null | undefined>>
```
</details>

- **Parameters**:
  - `v: ComputedRef<T>`
- **Return Type**: `v is ComputedRef<Exclude<T, null | undefined>>`

---

## Type Aliases

### `IsDefinedReturn`

```ts
type IsDefinedReturn = boolean;
```


---