[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `Menu.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---