[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useVirtualList/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useVirtualList` | `@vueuse/core` |
| `computed` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `itemHeight(i: any): any`

<details><summary>Code</summary>

```ts
i => (filteredItems.value[i].height + 8)
```
</details>

- **Parameters**:
  - `i: any`
- **Return Type**: `any`
### `itemHeight(i: any): any`

<details><summary>Code</summary>

```ts
i => (filteredItems.value[i].height + 8)
```
</details>

- **Parameters**:
  - `i: any`
- **Return Type**: `any`
### `handleScrollTo(): void`

<details><summary>Code</summary>

```ts
function handleScrollTo() {
  if (index.value)
    scrollTo(index.value)
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `scrollTo`

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