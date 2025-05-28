[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 1 |
| 📊 Variables & Constants | 1 |
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
📂 **`packages/core/useMemory/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useMemory` | `@vueuse/core` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `kb` | `number` | const | `v / 1024 / 1024` | ✗ |


---

## Functions

### `size(v: number): string`

<details><summary>Code</summary>

```ts
function size(v: number) {
  const kb = v / 1024 / 1024
  return `${kb.toFixed(2)} MB`
}
```
</details>

- **Parameters**:
  - `v: number`
- **Return Type**: `string`
- **Calls**:
  - `kb.toFixed`

---