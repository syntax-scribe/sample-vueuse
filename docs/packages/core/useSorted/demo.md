[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---