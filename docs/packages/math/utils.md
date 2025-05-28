[⬅️ Back to Table of Contents](../../index.md)

# 📄 `utils.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Type Aliases

### `MaybeComputedRefArgs<T>`

```ts
type MaybeComputedRefArgs<T> = MaybeRefOrGetter<T>[] | [MaybeRefOrGetter<MaybeRefOrGetter<T>[]>];
```


---