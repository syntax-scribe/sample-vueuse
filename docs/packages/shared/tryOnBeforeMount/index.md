[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/tryOnBeforeMount/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `../utils` |
| `nextTick` | `vue` |
| `onBeforeMount` | `vue` |
| `getLifeCycleTarget` | `../utils` |


---

## Functions

### `tryOnBeforeMount(fn: Fn, sync: boolean, target: any): void`

<details><summary>Code</summary>

```ts
export function tryOnBeforeMount(fn: Fn, sync = true, target?: any) {
  const instance = getLifeCycleTarget(target)
  if (instance)
    onBeforeMount(fn, target)
  else if (sync)
    fn()
  else
    nextTick(fn)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Call onBeforeMount() if it's inside a component lifecycle, if not, just call the function
 *
 * @param fn
 * @param sync if set to false, it will run in the nextTick() of Vue
 * @param target
 */
```

- **Parameters**:
  - `fn: Fn`
  - `sync: boolean`
  - `target: any`
- **Return Type**: `void`
- **Calls**:
  - `getLifeCycleTarget (from ../utils)`
  - `onBeforeMount (from vue)`
  - `fn`
  - `nextTick (from vue)`

---