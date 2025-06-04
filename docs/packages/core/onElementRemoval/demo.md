[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/onElementRemoval/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `onElementRemoval` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `demo1Ref` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |
| `demo2ParentRef` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |
| `demo2Ref` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |


---

## Functions

### `demo1BtnOnClick(): void`

<details><summary>Code</summary>

```ts
function demo1BtnOnClick() {
  demo1State.value = !demo1State.value
}
```
</details>

- **Return Type**: `void`
### `demo2BtnOnClick(): void`

<details><summary>Code</summary>

```ts
function demo2BtnOnClick() {
  demo2State.value = !demo2State.value
  if (demo2State.value) {
    demo2ParentRef.value?.appendChild(demo2Ref.value!)
  }
  else {
    demo2Ref.value?.remove()
  }
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `demo2ParentRef.value?.appendChild`
  - `demo2Ref.value?.remove`

---