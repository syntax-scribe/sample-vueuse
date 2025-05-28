[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.client.vue`

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
📂 **`packages/core/useShare/demo.client.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useShare` | `@vueuse/core` |
| `isClient` | `@vueuse/shared` |
| `deepRef` | `vue` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `startShare` | *none* | share().catch |


---

## Functions

### `startShare(): any`

<details><summary>Code</summary>

```ts
function startShare() {
  return share().catch(err => err)
}
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `share().catch`

---