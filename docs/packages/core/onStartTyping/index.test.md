[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/onStartTyping/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `shallowRef` | `vue` |
| `onStartTyping` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `element` | `Ref<HTMLInputElement>` | let/var | `*not shown*` | ✗ |
| `callBackFn` | `any` | let/var | `*not shown*` | ✗ |
| `ev` | `KeyboardEvent` | const | `new KeyboardEvent('keydown', { keyCode })` | ✗ |


---

## Functions

### `dispatchKeyDownEvent(keyCode: number): void`

<details><summary>Code</summary>

```ts
function dispatchKeyDownEvent(keyCode: number) {
    const ev = new KeyboardEvent('keydown', { keyCode })
    document.dispatchEvent(ev)
  }
```
</details>

- **Parameters**:
  - `keyCode: number`
- **Return Type**: `void`
- **Calls**:
  - `document.dispatchEvent`
### `range(size: number, startAt: number): number[]`

<details><summary>Code</summary>

```ts
function range(size: number, startAt = 0) {
    return [...Array.from({ length: size }).keys()].map(i => i + startAt)
  }
```
</details>

- **Parameters**:
  - `size: number`
  - `startAt: number`
- **Return Type**: `number[]`
- **Calls**:
  - `[...Array.from({ length: size }).keys()].map`
  - `Array.from({ length: size }).keys`

---