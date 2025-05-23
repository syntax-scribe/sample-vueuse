[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---