[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `Menu.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 4 |

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