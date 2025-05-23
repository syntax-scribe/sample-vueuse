[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/tryOnScopeDispose/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `../utils` |
| `getCurrentScope` | `vue` |
| `onScopeDispose` | `vue` |


---

## Functions

### `tryOnScopeDispose(fn: Fn): boolean`

<details><summary>Code</summary>

```ts
export function tryOnScopeDispose(fn: Fn) {
  if (getCurrentScope()) {
    onScopeDispose(fn)
    return true
  }
  return false
}
```
</details>

- **JSDoc**:
```ts
/**
 * Call onScopeDispose() if it's inside an effect scope lifecycle, if not, do nothing
 *
 * @param fn
 */
```

- **Parameters**:
  - `fn: Fn`
- **Return Type**: `boolean`
- **Calls**:
  - `getCurrentScope (from vue)`
  - `onScopeDispose (from vue)`

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