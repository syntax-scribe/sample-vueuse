[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `vue.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/utils/vue.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `getCurrentInstance` | `vue` |


---

## Functions

### `getLifeCycleTarget(target: any): any`

<details><summary>Code</summary>

```ts
export function getLifeCycleTarget(target?: any) {
  return target || getCurrentInstance()
}
```
</details>

- **Parameters**:
  - `target: any`
- **Return Type**: `any`
- **Calls**:
  - `getCurrentInstance (from vue)`

---