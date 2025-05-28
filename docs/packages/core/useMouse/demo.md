[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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