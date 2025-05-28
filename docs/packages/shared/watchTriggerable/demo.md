[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 1 |
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
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/watchTriggerable/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `watchTriggerable` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `canceled` | `boolean` | let/var | `false` | ✗ |


---

## Functions

### `clear(): void`

<details><summary>Code</summary>

```ts
function clear() {
  ignoreUpdates(() => {
    source.value = 0
    log.value = ''
  })
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `ignoreUpdates`
### `update(): void`

<details><summary>Code</summary>

```ts
function update() {
  source.value++
}
```
</details>

- **Return Type**: `void`

---