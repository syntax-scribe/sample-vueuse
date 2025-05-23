[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.client.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useShare/demo.client.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useShare` | `@vueuse/core` |
| `isClient` | `@vueuse/shared` |
| `deepRef` | `vue` |


---

## Functions

### `startShare(): any`

<details><summary>Code</summary>

```ts
function startShare() {
  return share().catch(err => err)
}
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `share().catch`

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