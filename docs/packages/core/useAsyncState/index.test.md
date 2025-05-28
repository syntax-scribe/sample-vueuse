[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 2 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useAsyncState/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `promiseTimeout` | `@vueuse/shared` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useAsyncState` | `./index` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `p1` | *none* | new Promise(...) |
| async-function | `p2` | *none* | *none* |


---

## Functions

### `p1(num: number): Promise<unknown>`

<details><summary>Code</summary>

```ts
(num = 1) => {
    return new Promise((resolve) => {
      setTimeout(() => {
        resolve(num)
      }, 50)
    })
  }
```
</details>

- **Parameters**:
  - `num: number`
- **Return Type**: `Promise<unknown>`
- **Calls**:
  - `setTimeout`
  - `resolve`
### `p2(id: string): Promise<string>`

<details><summary>Code</summary>

```ts
async (id?: string) => {
    if (!id)
      throw new Error('error')
    return id
  }
```
</details>

- **Parameters**:
  - `id: string`
- **Return Type**: `Promise<string>`

---