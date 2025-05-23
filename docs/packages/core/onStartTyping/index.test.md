[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---