[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useDebouncedRefHistory/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `formatDate` | `@vueuse/core` |
| `useCounter` | `@vueuse/core` |
| `useDebouncedRefHistory` | `@vueuse/core` |
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