[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 13 |
| 📊 Variables & Constants | 18 |
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
📂 **`packages/shared/until/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Equal` | `@type-challenges/utils` |
| `Expect` | `@type-challenges/utils` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `invoke` | `@vueuse/shared` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `until` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `x` | `any` | let/var | `await until(r1).toBe(1)` | ✗ |
| `x` | `unknown[]` | let/var | `await until(r).changed()` | ✗ |
| `x` | `unknown[]` | let/var | `await until(r).changedTimes(3)` | ✗ |
| `x` | `any` | let/var | `await until(r).not.toBe(0)` | ✗ |
| `x` | `any` | let/var | `await instance.not.toBe(0)` | ✗ |
| `y` | `any` | let/var | `await instance.not.toBe(2)` | ✗ |
| `x` | `any` | let/var | `await until(r).not.toBeNull()` | ✗ |
| `x` | `unknown[]` | let/var | `await until(r).toContains(4, { deep: true })` | ✗ |
| `x` | `unknown[]` | let/var | `await until(r).not.toContains(2, { deep: true })` | ✗ |
| `one` | `any` | let/var | `await until(x).toBe(1 as const)` | ✗ |
| `xTruthy` | `any` | let/var | `await until(x).toBeTruthy()` | ✗ |
| `xFalsy` | `any` | let/var | `await until(x).not.toBeTruthy()` | ✗ |
| `xUndef` | `any` | let/var | `await until(x).toBeUndefined()` | ✗ |
| `xNotUndef` | `any` | let/var | `await until(x).not.toBeUndefined()` | ✗ |
| `yNull` | `any` | let/var | `await until(y).toBeNull()` | ✗ |
| `yNotNull` | `any` | let/var | `await until(y).not.toBeNull()` | ✗ |
| `z1` | `unknown[]` | let/var | `await until(z).toMatch(is1)` | ✗ |
| `zNot1` | `unknown[]` | let/var | `await until(z).not.toMatch(is1)` | ✗ |


---

## Functions

### `is1(x: number): x is 1`

<details><summary>Code</summary>

```ts
(x: number): x is 1 => x === 1
```
</details>

- **Parameters**:
  - `x: number`
- **Return Type**: `x is 1`

---