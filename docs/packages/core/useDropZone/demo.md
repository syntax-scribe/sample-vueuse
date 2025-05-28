[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useDropZone/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useDropZone` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `filesData` | `boolean` | let/var | `shallowRef<{ name: string, size: number, type: string, lastModified: number }[]>([])` | ✗ |
| `imageFilesData` | `boolean` | let/var | `shallowRef<{ name: string, size: number, type: string, lastModified: number }[]>([])` | ✗ |
| `dropZoneRef` | `boolean` | let/var | `useTemplateRef<HTMLElement>('dropZoneRef')` | ✗ |
| `imageDropZoneRef` | `boolean` | let/var | `useTemplateRef<HTMLElement>('imageDropZoneRef')` | ✗ |


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