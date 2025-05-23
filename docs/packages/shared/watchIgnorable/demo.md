[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---