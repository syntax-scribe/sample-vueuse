[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `rocketRef` | `boolean` | let/var | `useTemplateRef<HTMLDivElement>('rocketRef')` | ✗ |


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