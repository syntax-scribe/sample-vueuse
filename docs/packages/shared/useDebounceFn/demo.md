[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

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