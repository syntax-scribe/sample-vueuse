[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 2 |
| ⚡ Async/Await Patterns | 1 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useFileSystemAccess/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `reactify` | `@vueuse/core` |
| `useFileSystemAccess` | `@vueuse/core` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `YAML` | `yaml` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `dataType` | `ShallowRef<"ArrayBuffer" | "Text" | "Blob">` | let/var | `shallowRef('Text') as ShallowRef<'Text' | 'ArrayBuffer' | 'Blob'>` | ✗ |
| `content` | `any` | let/var | `res.data` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `onSave` | res.save() | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |


---

## Functions

### `onSave(): Promise<void>`

<details><summary>Code</summary>

```ts
async function onSave() {
  await res.save()
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `res.save`

---