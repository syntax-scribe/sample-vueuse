[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 2 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useSupported/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `computed` | `vue` |
| `useMounted` | `../useMounted` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useSupported(callback: () => unknown): any`

<details><summary>Code</summary>

```ts
export function useSupported(callback: () => unknown) {
  const isMounted = useMounted()

  return computed(() => {
    // to trigger the ref
    // eslint-disable-next-line ts/no-unused-expressions
    isMounted.value
    return Boolean(callback())
  })
}
```
</details>

- **Parameters**:
  - `callback: () => unknown`
- **Return Type**: `any`
- **Calls**:
  - `useMounted (from ../useMounted)`
  - `computed (from vue)`
  - `Boolean`
  - `callback`
- **Internal Comments**:
```
// to trigger the ref (x3)
// eslint-disable-next-line ts/no-unused-expressions (x3)
```


---

## Type Aliases

### `UseSupportedReturn`

```ts
type UseSupportedReturn = ReturnType<typeof useSupported>;
```


---