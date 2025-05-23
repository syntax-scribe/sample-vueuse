[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useDropZone/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useDropZone` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Functions

### `onDrop(files: File[] | null): void`

<details><summary>Code</summary>

```ts
function onDrop(files: File[] | null) {
  filesData.value = []
  if (files) {
    filesData.value = files.map(file => ({
      name: file.name,
      size: file.size,
      type: file.type,
      lastModified: file.lastModified,
    }))
  }
}
```
</details>

- **Parameters**:
  - `files: File[] | null`
- **Return Type**: `void`
- **Calls**:
  - `files.map`
### `onImageDrop(files: File[] | null): void`

<details><summary>Code</summary>

```ts
function onImageDrop(files: File[] | null) {
  imageFilesData.value = []
  if (files) {
    imageFilesData.value = files.map(file => ({
      name: file.name,
      size: file.size,
      type: file.type,
      lastModified: file.lastModified,
    }))
  }
}
```
</details>

- **Parameters**:
  - `files: File[] | null`
- **Return Type**: `void`
- **Calls**:
  - `files.map`

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