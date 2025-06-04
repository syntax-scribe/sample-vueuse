[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useRefHistory/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `formatDate` | `@vueuse/core` |
| `useCounter` | `@vueuse/core` |
| `useRefHistory` | `@vueuse/core` |


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