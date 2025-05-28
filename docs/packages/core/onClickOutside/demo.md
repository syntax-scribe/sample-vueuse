[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/onClickOutside/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `OnClickOutsideHandler` | `@vueuse/core` |
| `vOnClickOutside` | `@vueuse/components` |
| `onClickOutside` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Functions

### `dropdownHandler(event: any): void`

<details><summary>Code</summary>

```ts
(event) => {
  console.log(event)
  dropdown.value = false
}
```
</details>

- **Parameters**:
  - `event: any`
- **Return Type**: `void`
- **Calls**:
  - `console.log`

---