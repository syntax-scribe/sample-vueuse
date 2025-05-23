[⬅️ Back to Table of Contents](../../index.md)

# 📄 `metadata.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/metadata/metadata.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `PackageIndexes` | `./types` |
| `_categories` | `./index.json` |
| `_functions` | `./index.json` |
| `_packages` | `./index.json` |
| `_metadata` | `./index.json` |


---

## Functions

### `getFunction(name: string): VueUseFunction`

<details><summary>Code</summary>

```ts
export function getFunction(name: string) {
  return metadata.functions.find(f => f.name === name)
}
```
</details>

- **Parameters**:
  - `name: string`
- **Return Type**: `VueUseFunction`
- **Calls**:
  - `metadata.functions.find`

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