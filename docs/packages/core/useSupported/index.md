[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useSupported/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `computed` | `vue` |
| `useMounted` | `../useMounted` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseSupportedReturn`

```ts
type UseSupportedReturn = ReturnType<typeof useSupported>;
```


---