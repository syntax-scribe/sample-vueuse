[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 1 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 5 |
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
- [Classes](#classes)

## 🛠️ File Location:
📂 **`packages/core/useFileDialog/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `shallowRef` | `vue` |
| `useFileDialog` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `file1` | `File` | const | `new File(['content1'], 'file1.txt', { type: 'text/plain' })` | ✗ |
| `file2` | `File` | const | `new File(['content2'], 'file2.txt', { type: 'text/plain' })` | ✗ |
| `initialFiles` | `DataTransfer` | const | `new DataTransfer()` | ✗ |
| `expectedFiles` | `DataTransfer` | const | `new DataTransfer()` | ✗ |
| `file` | `File` | let/var | `new File(['dummy content'], 'example.txt', { type: 'text/plain' })` | ✗ |


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

### `DataTransferMock`

<details><summary>Class Code</summary>

```ts
class DataTransferMock {
  items = new Set()

  get files() {
    return this.items.values()
  }
}
```
</details>


---