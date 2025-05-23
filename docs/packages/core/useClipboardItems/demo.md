[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useClipboardItems/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useClipboardItems` | `@vueuse/core` |
| `usePermission` | `@vueuse/core` |
| `effect` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `createClipboardItems(text: string): ClipboardItem`

<details><summary>Code</summary>

```ts
function createClipboardItems(text: string) {
  const mime = 'text/plain'
  const blob = new Blob([text], { type: mime })
  return new ClipboardItem({
    [mime]: blob,
  })
}
```
</details>

- **Parameters**:
  - `text: string`
- **Return Type**: `ClipboardItem`

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