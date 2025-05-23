[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useScroll/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useScroll` | `@vueuse/core` |
| `computed` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `toRefs` | `vue` |
| `useTemplateRef` | `vue` |


---

## Functions

### `updateScrollPosition(): void`

<details><summary>Code</summary>

```ts
function updateScrollPosition() {
  height.value = height.value === 'h-[500px]' ? 'h-[200px]' : 'h-[500px]'
  nextTick(() => {
    measure()
  })
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `nextTick (from vue)`
  - `measure`

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