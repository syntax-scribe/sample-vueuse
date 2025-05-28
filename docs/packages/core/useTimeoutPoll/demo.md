[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
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

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useTimeoutPoll/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `promiseTimeout` | `@vueuse/core` |
| `useTimeoutPoll` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `fetchData` | promiseTimeout(1000) | *none* |


---

## Functions

### `fetchData(): Promise<void>`

<details><summary>Code</summary>

```ts
async function fetchData() {
  await promiseTimeout(1000)
  count.value++
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `promiseTimeout (from @vueuse/core)`

---