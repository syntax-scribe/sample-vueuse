[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 6 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useBase64/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `useBase64` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `template` | `{ test: number; }` | let/var | `{ test: 5 }` | ✗ |
| `map` | `Map<string, number>` | let/var | `new Map([['test', 1]])` | ✗ |
| `set` | `Set<number>` | let/var | `new Set([1])` | ✗ |
| `arr` | `number[]` | let/var | `[1, 2, 3]` | ✗ |
| `arr` | `number[]` | let/var | `[1, 2, 3]` | ✗ |
| `arr` | `number[]` | let/var | `[1, 2, 3]` | ✗ |


---

## Functions

### `serializer(arr: number[]): string`

<details><summary>Code</summary>

```ts
(arr: number[]) => {
      return JSON.stringify(arr.map(el => el * 2))
    }
```
</details>

- **Parameters**:
  - `arr: number[]`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
  - `arr.map`

---