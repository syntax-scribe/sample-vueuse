[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/electron/useZoomFactor/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WebFrame` | `electron` |
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `deepRef` | `vue` |
| `isRef` | `vue` |
| `watch` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `webFrame` | `WebFrame | undefined` | let/var | `*not shown*` | ✗ |
| `newFactor` | `Ref<number> | null` | let/var | `null` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useZoomFactor(factor: MaybeRef<number>): Ref<number>`

<details><summary>Code</summary>

```ts
export function useZoomFactor(factor: MaybeRef<number>): Ref<number>
```
</details>

- **Parameters**:
  - `factor: MaybeRef<number>`
- **Return Type**: `Ref<number>`

---