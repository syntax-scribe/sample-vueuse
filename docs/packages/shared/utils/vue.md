[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `vue.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 1
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---