[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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