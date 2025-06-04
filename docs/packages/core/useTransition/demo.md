[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useTransition/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `rand` | `@vueuse/core` |
| `TransitionPresets` | `@vueuse/core` |
| `useTransition` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `duration` | `1500` | let/var | `1500` | ✗ |


---

## Functions

### `easeOutElastic(n: number): number`

<details><summary>Code</summary>

```ts
function easeOutElastic(n: number) {
  return n === 0
    ? 0
    : n === 1
      ? 1
      : (2 ** (-10 * n)) * Math.sin((n * 10 - 0.75) * ((2 * Math.PI) / 3)) + 1
}
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `number`
- **Calls**:
  - `Math.sin`
### `toggle(): void`

<details><summary>Code</summary>

```ts
function toggle() {
  baseNumber.value = baseNumber.value === 100 ? 0 : 100
  baseVector.value = [rand(0, 100), rand(0, 100)]
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `rand (from @vueuse/core)`

---