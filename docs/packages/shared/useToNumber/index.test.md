[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

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