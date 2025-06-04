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
📂 **`packages/shared/tryOnBeforeUnmount/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `../utils` |
| `onBeforeUnmount` | `vue` |
| `getLifeCycleTarget` | `../utils` |


---

## Functions

### `tryOnBeforeUnmount(fn: Fn, target: any): void`

<details><summary>Code</summary>

```ts
export function tryOnBeforeUnmount(fn: Fn, target?: any) {
  const instance = getLifeCycleTarget(target)
  if (instance)
    onBeforeUnmount(fn, target)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Call onBeforeUnmount() if it's inside a component lifecycle, if not, do nothing
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
  - `onBeforeUnmount (from vue)`

---