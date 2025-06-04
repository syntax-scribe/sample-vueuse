[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useVirtualList/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useVirtualList` | `@vueuse/core` |
| `computed` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `index` | `boolean` | let/var | `shallowRef<number>()` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `itemHeight(i: any): any`

<details><summary>Code</summary>

```ts
i => (filteredItems.value[i].height + 8)
```
</details>

- **Parameters**:
  - `i: any`
- **Return Type**: `any`
### `itemHeight(i: any): any`

<details><summary>Code</summary>

```ts
i => (filteredItems.value[i].height + 8)
```
</details>

- **Parameters**:
  - `i: any`
- **Return Type**: `any`
### `handleScrollTo(): void`

<details><summary>Code</summary>

```ts
function handleScrollTo() {
  if (index.value)
    scrollTo(index.value)
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `scrollTo`

---