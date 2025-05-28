[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useSorted/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `rand` | `@vueuse/core` |
| `useSorted` | `@vueuse/core` |
| `computed` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `objArr` | `{ name: string; age: number; }[]` | let/var | `[{
  name: 'John',
  age: 40,
}, {
  name: 'Jane',
  age: 20,
}, {
  name: 'Joe',
  age: 30,
}, {
  name: 'Jenny',
  age: 22,
}]` | ✗ |
| `arr` | `any[]` | let/var | `[]` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `randomArr(): void`

<details><summary>Code</summary>

```ts
function randomArr() {
  const arr = []
  for (let i = 0; i < rand(10, 20); i++)
    arr.push(rand(0, 100))
  arrText.value = arr.join(',')
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `rand (from @vueuse/core)`
  - `arr.push`
  - `arr.join`

---