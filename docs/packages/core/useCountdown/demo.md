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
📂 **`packages/core/useCountdown/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useCountdown` | `@vueuse/core` |
| `useEventListener` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Functions

### `startCountdown(): void`

<details><summary>Code</summary>

```ts
function startCountdown() {
  rocketRef.value!.classList.remove('launching')
  start(countdownSeconds)
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `rocketRef.value!.classList.remove`
  - `start`

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