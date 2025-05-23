[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

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
📂 **`packages/core/useWakeLock/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useWakeLock` | `@vueuse/core` |
| `computed` | `vue` |
| `reactive` | `vue` |


---

## Functions

### `onClick(): any`

<details><summary>Code</summary>

```ts
function onClick() {
  return wakeLock.isActive ? wakeLock.release() : wakeLock.request('screen')
}
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `wakeLock.release`
  - `wakeLock.request`

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