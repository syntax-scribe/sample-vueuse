[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/useDebounceFn/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useDebounceFn` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Functions

### `clickedFn(): void`

<details><summary>Code</summary>

```ts
function clickedFn() {
  clicked.value += 1
  debouncedFn()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `debouncedFn`

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