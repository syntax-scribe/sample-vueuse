[⬅️ Back to Table of Contents](../../index.md)

# 📄 `nextTick.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 0 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 1 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/.test/nextTick.ts`**

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `nextTwoTick` | *none* | new Promise(...) |


---

## Functions

### `nextTwoTick(): Promise<void>`

<details><summary>Code</summary>

```ts
export function nextTwoTick() {
  return new Promise<void>((resolve) => {
    setTimeout(() => {
      setTimeout(resolve)
    })
  })
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `setTimeout`

---