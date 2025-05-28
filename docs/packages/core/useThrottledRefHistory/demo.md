[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 0 |
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
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useThrottledRefHistory/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `formatDate` | `@vueuse/core` |
| `useCounter` | `@vueuse/core` |
| `useThrottledRefHistory` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Functions

### `format(ts: number): any`

<details><summary>Code</summary>

```ts
function format(ts: number) {
  return formatDate(new Date(ts), 'YYYY-MM-DD HH:mm:ss')
}
```
</details>

- **Parameters**:
  - `ts: number`
- **Return Type**: `any`
- **Calls**:
  - `formatDate (from @vueuse/core)`

---