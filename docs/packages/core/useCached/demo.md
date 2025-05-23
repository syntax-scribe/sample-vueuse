[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useCached/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useCached` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Functions

### `comparator(a: Value, b: Value): boolean`

<details><summary>Code</summary>

```ts
function comparator(a: Value, b: Value) {
  return a.value === b.value
}
```
</details>

- **Parameters**:
  - `a: Value`
  - `b: Value`
- **Return Type**: `boolean`
### `onSyncClick(): void`

<details><summary>Code</summary>

```ts
function onSyncClick() {
  value.value = {
    value: inputValue.value,
    extra: inputExtra.value,
  }
}
```
</details>

- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `Value`

<details><summary>Interface Code</summary>

```ts
interface Value {
  value: number
  extra: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `value` | `number` | ✗ |  |
| `extra` | `number` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---