[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
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
📂 **`packages/core/useClipboardItems/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useClipboardItems` | `@vueuse/core` |
| `usePermission` | `@vueuse/core` |
| `effect` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `mime` | `"text/plain"` | let/var | `'text/plain'` | ✗ |
| `blob` | `Blob` | let/var | `new Blob([text], { type: mime })` | ✗ |


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