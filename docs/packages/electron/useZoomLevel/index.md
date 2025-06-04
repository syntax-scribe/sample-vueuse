[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/electron/useZoomLevel/index.ts`**

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
| `newLevel` | `Ref<number> | null` | let/var | `null` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useZoomLevel(level: MaybeRef<number>): Ref<number>`

<details><summary>Code</summary>

```ts
export function useZoomLevel(level: MaybeRef<number>): Ref<number>
```
</details>

- **Parameters**:
  - `level: MaybeRef<number>`
- **Return Type**: `Ref<number>`

---