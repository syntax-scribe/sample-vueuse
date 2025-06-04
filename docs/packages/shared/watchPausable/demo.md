[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/watchPausable/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `onStartTyping` | `@vueuse/core` |
| `watchPausable` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `input` | `number` | let/var | `shallowRef<HTMLInputElement | null>()` | ✗ |


---

## Functions

### `clear(): void`

<details><summary>Code</summary>

```ts
function clear() {
  log.value = ''
}
```
</details>

- **Return Type**: `void`
### `pause(): void`

<details><summary>Code</summary>

```ts
function pause() {
  log.value += 'Paused\n'
  watcher.pause()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `watcher.pause`
### `resume(): void`

<details><summary>Code</summary>

```ts
function resume() {
  log.value += 'Resumed\n'
  watcher.resume()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `watcher.resume`

---