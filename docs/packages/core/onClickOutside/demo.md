[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |

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