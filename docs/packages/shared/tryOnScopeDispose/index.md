[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

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