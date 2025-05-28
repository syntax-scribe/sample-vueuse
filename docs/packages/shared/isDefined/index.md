[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
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