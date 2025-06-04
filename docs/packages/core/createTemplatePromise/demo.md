[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 1 |
| 📊 Variables & Constants | 2 |
| ⚡ Async/Await Patterns | 2 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/createTemplatePromise/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `createTemplatePromise` | `@vueuse/core` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `TemplatePromise` | `boolean` | let/var | `createTemplatePromise<DialogResult` | ✗ |
| `result` | `any` | let/var | `await TemplatePromise.start(`Hello ${idx}`)` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `open` | TemplatePromise.start(`Hello ${idx}`) | *none* |
| promise-chain | `asyncFn` | *none* | new Promise(...) |


---

## Functions

### `open(idx: number): Promise<void>`

<details><summary>Code</summary>

```ts
async function open(idx: number) {
  console.log(idx, 'Before')
  const result = await TemplatePromise.start(`Hello ${idx}`)
  console.log(idx, 'After', result)
}
```
</details>

- **Parameters**:
  - `idx: number`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `console.log`
  - `TemplatePromise.start`
### `asyncFn(): boolean`

<details><summary>Code</summary>

```ts
function asyncFn() {
  return new Promise<DialogResult>((resolve) => {
    setTimeout(() => {
      resolve('ok')
    }, 1000)
  })
}
```
</details>

- **Return Type**: `boolean`
- **Calls**:
  - `setTimeout`
  - `resolve`

---

## Type Aliases

### `DialogResult`

```ts
type DialogResult = 'ok' | 'cancel';
```


---