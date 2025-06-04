[⬅️ Back to Table of Contents](../../index.md)

# 📄 `metadata.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 5 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `categoriesOrder` | `string[]` | const | `[
  'State',
  'Elements',
  'Browser',
  'Sensors',
  'Network',
  'Animation',
  'Component',
  'Watch',
  'Reactivity',
  'Array',
  'Time',
  'Utilities',
]` | ✗ |
| `metadata` | `PackageIndexes` | const | `_metadata as PackageIndexes` | ✓ |
| `functions` | `VueUseFunction[]` | const | `_functions as PackageIndexes['functions']` | ✓ |
| `packages` | `Record<string, VueUsePackage>` | const | `_packages as PackageIndexes['packages']` | ✓ |
| `categories` | `string[]` | const | `_categories as PackageIndexes['categories']` | ✓ |


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