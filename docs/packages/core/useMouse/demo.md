[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 6 |
| 🟢 Vue Composition API | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useMouse/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseMouseEventExtractor` | `@vueuse/core` |
| `reactify` | `@vueuse/core` |
| `useMouse` | `@vueuse/core` |
| `useParentElement` | `@vueuse/core` |
| `reactive` | `vue` |
| `YAML` | `yaml` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


---

## Functions

### `extractor(event: any): number[]`

<details><summary>Code</summary>

```ts
(event) => {
  if (event instanceof MouseEvent)
    return [event.offsetX, event.offsetY]
  else
    return null
}
```
</details>

- **Parameters**:
  - `event: any`
- **Return Type**: `number[]`

---