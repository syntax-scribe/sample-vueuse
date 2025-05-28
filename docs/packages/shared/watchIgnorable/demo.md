[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
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
📂 **`packages/shared/watchIgnorable/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `watchIgnorable` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Functions

### `clear(): void`

<details><summary>Code</summary>

```ts
function clear() {
  source.value = 0
  log.value = ''
}
```
</details>

- **Return Type**: `void`
### `update(): void`

<details><summary>Code</summary>

```ts
function update() {
  source.value++
}
```
</details>

- **Return Type**: `void`
### `ignoredUpdate(): void`

<details><summary>Code</summary>

```ts
function ignoredUpdate() {
  ignoreUpdates(() => {
    source.value++
  })
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `ignoreUpdates`

---