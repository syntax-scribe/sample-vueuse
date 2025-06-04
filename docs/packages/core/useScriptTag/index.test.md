[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `src` | `"https://code.jquery.com/jquery-3.5.1.min.js"` | const | `'https://code.jquery.com/jquery-3.5.1.min.js'` | ✗ |


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