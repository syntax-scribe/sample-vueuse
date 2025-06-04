[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useTextDirection/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useTextDirection` | `@vueuse/core` |
| `computed` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `handleOnClick(): void`

<details><summary>Code</summary>

```ts
function handleOnClick() {
  dir.value = dir.value === 'rtl' ? 'ltr' : 'rtl'
}
```
</details>

- **Return Type**: `void`

---