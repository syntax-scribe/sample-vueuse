[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/watchTriggerable/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `watchTriggerable` | `@vueuse/core` |
| `shallowRef` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---