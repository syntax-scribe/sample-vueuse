[⬅️ Back to Table of Contents](../../index.md)

# 📄 `app.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`playgrounds/nuxt/app.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useColorMode` | `@vueuse/core` |
| `useWindowSize` | `@vueuse/core` |
| `onMounted` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |


---

## Functions

### `toggleMode(): void`

<details><summary>Code</summary>

```ts
function toggleMode() {
  state.color = state.color === 'light' ? 'dark' : 'light'
}
```
</details>

- **Return Type**: `void`

---