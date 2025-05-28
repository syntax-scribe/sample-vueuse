[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 0 |
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