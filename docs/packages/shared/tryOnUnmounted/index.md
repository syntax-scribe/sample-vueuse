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
📂 **`packages/shared/tryOnUnmounted/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `../utils` |
| `onUnmounted` | `vue` |
| `getLifeCycleTarget` | `../utils` |


---

## Functions

### `tryOnUnmounted(fn: Fn, target: any): void`

<details><summary>Code</summary>

```ts
export function tryOnUnmounted(fn: Fn, target?: any) {
  const instance = getLifeCycleTarget(target)
  if (instance)
    onUnmounted(fn, target)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Call onUnmounted() if it's inside a component lifecycle, if not, do nothing
 *
 * @param fn
 * @param target
 */
```

- **Parameters**:
  - `fn: Fn`
  - `target: any`
- **Return Type**: `void`
- **Calls**:
  - `getLifeCycleTarget (from ../utils)`
  - `onUnmounted (from vue)`

---