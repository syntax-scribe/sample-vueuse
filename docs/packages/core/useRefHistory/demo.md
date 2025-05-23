[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---