[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `Menu.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
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
📂 **`packages/core/useMediaControls/components/Menu.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `onClickOutside` | `@vueuse/core` |
| `useEventListener` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Functions

### `open(): boolean`

<details><summary>Code</summary>

```ts
function open() {
  return isOpen.value = true
}
```
</details>

- **Return Type**: `boolean`
### `close(): boolean`

<details><summary>Code</summary>

```ts
function close() {
  return isOpen.value = false
}
```
</details>

- **Return Type**: `boolean`

---