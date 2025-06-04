[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 2 |

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