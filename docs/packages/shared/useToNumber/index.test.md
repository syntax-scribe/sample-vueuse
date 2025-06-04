[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/useToNumber/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `shallowRef` | `vue` |
| `useToNumber` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `warn` | `string` | let/var | `''` | ✗ |


---

## Functions

### `method(v: string | number): number`

<details><summary>Code</summary>

```ts
(v) => {
      if (!Number.isSafeInteger(Number(v))) {
        warnFn('Value is not a safe integer')
      }
      return 0
    }
```
</details>

- **Parameters**:
  - `v: string | number`
- **Return Type**: `number`
- **Calls**:
  - `Number.isSafeInteger`
  - `Number`
  - `warnFn`
### `method(v: string | number): number`

<details><summary>Code</summary>

```ts
(v) => {
      if (!Number.isSafeInteger(Number(v))) {
        warnFn('Value is not a safe integer')
      }
      return 0
    }
```
</details>

- **Parameters**:
  - `v: string | number`
- **Return Type**: `number`
- **Calls**:
  - `Number.isSafeInteger`
  - `Number`
  - `warnFn`
### `method(v: string | number): number`

<details><summary>Code</summary>

```ts
(v) => {
      if (!Number.isSafeInteger(Number(v))) {
        warnFn('Value is not a safe integer')
      }
      return 0
    }
```
</details>

- **Parameters**:
  - `v: string | number`
- **Return Type**: `number`
- **Calls**:
  - `Number.isSafeInteger`
  - `Number`
  - `warnFn`
### `method(v: string | number): number`

<details><summary>Code</summary>

```ts
(v) => {
      if (!Number.isSafeInteger(Number(v))) {
        warnFn('Value is not a safe integer')
      }
      return 0
    }
```
</details>

- **Parameters**:
  - `v: string | number`
- **Return Type**: `number`
- **Calls**:
  - `Number.isSafeInteger`
  - `Number`
  - `warnFn`

---