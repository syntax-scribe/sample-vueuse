[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `IsDefinedReturn`

```ts
type IsDefinedReturn = boolean;
```


---