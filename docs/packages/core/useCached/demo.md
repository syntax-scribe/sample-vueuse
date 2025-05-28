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
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useCached/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useCached` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `value` | `boolean` | let/var | `shallowRef<Value>({ value: 42, extra: 0 })` | ✗ |


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