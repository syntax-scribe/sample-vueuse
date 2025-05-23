[⬅️ Back to Table of Contents](../../index.md)

# 📄 `utils.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/math/utils.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `toValueArgsFlat(args: MaybeComputedRefArgs<T>): T[]`

<details><summary>Code</summary>

```ts
export function toValueArgsFlat<T>(args: MaybeComputedRefArgs<T>): T[] {
  return args
    .flatMap((i: any) => {
      const v = toValue(i)
      if (Array.isArray(v))
        return v.map(i => toValue(i))
      return [v]
    })
}
```
</details>

- **Parameters**:
  - `args: MaybeComputedRefArgs<T>`
- **Return Type**: `T[]`
- **Calls**:
  - `args
    .flatMap`
  - `toValue (from vue)`
  - `Array.isArray`
  - `v.map`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `MaybeComputedRefArgs<T>`

```ts
type MaybeComputedRefArgs<T> = MaybeRefOrGetter<T>[] | [MaybeRefOrGetter<MaybeRefOrGetter<T>[]>];
```


---