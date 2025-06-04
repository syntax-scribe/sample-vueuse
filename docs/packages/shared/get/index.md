[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/get/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `../utils` |
| `unref` | `vue` |


---

## Functions

### `get(ref: MaybeRef<T>): T`

<details><summary>Code</summary>

```ts
export function get<T>(ref: MaybeRef<T>): T
```
</details>

- **JSDoc**:
```ts
/**
 * Shorthand for accessing `ref.value`
 */
```

- **Parameters**:
  - `ref: MaybeRef<T>`
- **Return Type**: `T`

---