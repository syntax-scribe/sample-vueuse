[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/useDateFormat/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `formatDate` | `./index` |
| `normalizeDate` | `./index` |
| `useDateFormat` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `date` | `Date` | const | `new Date(2022, 0, 1, 0, 0, 0)` | ✗ |
| `m` | `"μμ" | "ΜΜ" | "πμ" | "ΠΜ"` | const | `hours > 11 ? (isLowercase ? 'μμ' : 'ΜΜ') : (isLowercase ? 'πμ' : 'ΠΜ')` | ✗ |


---

## Functions

### `customMeridiem(hours: number, minutes: number, isLowercase: boolean, hasPeriod: boolean): string`

<details><summary>Code</summary>

```ts
(hours: number, minutes: number, isLowercase?: boolean, hasPeriod?: boolean) => {
      const m = hours > 11 ? (isLowercase ? 'μμ' : 'ΜΜ') : (isLowercase ? 'πμ' : 'ΠΜ')
      return hasPeriod ? m.split('').reduce((acc, curr) => acc += `${curr}.`, '') : m
    }
```
</details>

- **Parameters**:
  - `hours: number`
  - `minutes: number`
  - `isLowercase: boolean`
  - `hasPeriod: boolean`
- **Return Type**: `string`
- **Calls**:
  - `m.split('').reduce`

---