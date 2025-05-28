[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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