[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 1
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/createTemplatePromise/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `createTemplatePromise` | `@vueuse/core` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `DialogResult`

```ts
type DialogResult = 'ok' | 'cancel';
```


---