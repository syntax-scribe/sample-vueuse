[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useTimeoutPoll/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `promiseTimeout` | `@vueuse/core` |
| `useTimeoutPoll` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Functions

### `fetchData(): Promise<void>`

<details><summary>Code</summary>

```ts
async function fetchData() {
  await promiseTimeout(1000)
  count.value++
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `promiseTimeout (from @vueuse/core)`

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