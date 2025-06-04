[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useCached/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `isShallow` | `vue` |
| `shallowRef` | `vue` |
| `nextTwoTick` | `../../.test` |
| `useCached` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `initialArrayValue` | `any` | let/var | `arrayRef.value` | ✗ |


---

## Functions

### `arrayEquals(a: T[], b: T[]): boolean`

<details><summary>Code</summary>

```ts
function arrayEquals<T>(a: T[], b: T[]): boolean {
  if (a.length !== b.length)
    return false

  for (let i = 0; i < a.length; i++) {
    if (a[i] !== b[i])
      return false
  }
  return true
}
```
</details>

- **Parameters**:
  - `a: T[]`
  - `b: T[]`
- **Return Type**: `boolean`

---