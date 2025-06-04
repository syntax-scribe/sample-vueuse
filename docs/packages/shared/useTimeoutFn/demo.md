[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/useTimeoutFn/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useTimeoutFn` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `defaultText` | `"Please wait for 3 seconds"` | let/var | `'Please wait for 3 seconds'` | ✗ |


---

## Functions

### `restart(): void`

<details><summary>Code</summary>

```ts
function restart() {
  text.value = defaultText
  start()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `start`

---