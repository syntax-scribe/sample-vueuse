[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/watchPausable/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `onStartTyping` | `@vueuse/core` |
| `watchPausable` | `@vueuse/core` |
| `shallowRef` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---