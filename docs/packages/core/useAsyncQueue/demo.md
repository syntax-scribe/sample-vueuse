[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 1 |
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
📂 **`packages/core/useAsyncQueue/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useAsyncQueue` | `@vueuse/core` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `p1` | *none* | new Promise(...) |
| promise-chain | `p2` | *none* | new Promise(...) |


---

## Functions

### `p1(): Promise<any>`

<details><summary>Code</summary>

```ts
function p1() {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(1000)
    }, 10)
  })
}
```
</details>

- **Return Type**: `Promise<any>`
- **Calls**:
  - `setTimeout`
  - `resolve`
### `p2(result: number): Promise<any>`

<details><summary>Code</summary>

```ts
function p2(result: number) {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve(1000 + result)
    }, 20)
  })
}
```
</details>

- **Parameters**:
  - `result: number`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `setTimeout`
  - `resolve`

---