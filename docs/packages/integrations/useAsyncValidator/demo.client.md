[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.client.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 1 |
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

## 🛠️ File Location:
📂 **`packages/integrations/useAsyncValidator/demo.client.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Rules` | `async-validator` |
| `useAsyncValidator` | `@vueuse/integrations` |
| `reactive` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `rules` | `Rules` | let/var | `{
  name: {
    type: 'string',
    min: 5,
    max: 20,
    required: true,
  },
  age: {
    type: 'number',
    required: true,
  },
  email: [
    {
      type: 'email',
      required: true,
    },
  ],
}` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |


---

## 🔧 Functions

> No functions found in this file.


---