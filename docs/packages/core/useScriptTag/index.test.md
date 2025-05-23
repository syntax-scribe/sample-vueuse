[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useScriptTag/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useSetup` | `../../.test` |
| `useScriptTag` | `./index` |


---

## Functions

### `scriptTagElement(): HTMLScriptElement | null`

<details><summary>Code</summary>

```ts
(): HTMLScriptElement | null =>
    document.head.querySelector(`script[src="${src}"]`)
```
</details>

- **Return Type**: `HTMLScriptElement | null`
- **Calls**:
  - `document.head.querySelector`

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