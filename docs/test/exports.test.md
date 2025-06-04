[⬅️ Back to Table of Contents](../index.md)

# 📄 `exports.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`test/exports.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `x` | `tinyexec` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `getPackageExportsManifest` | `vitest-package-exports` |
| `yaml` | `yaml` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `manifest` | `any` | let/var | `await getPackageExportsManifest({
        importMode: 'src',
        cwd: pkg.path,
      })` | ✗ |


---

## Functions

### `sortMapEntries(a: any, b: any): number`

<details><summary>Code</summary>

```ts
(a, b) => String(a.key).localeCompare(String(b.key))
```
</details>

- **Parameters**:
  - `a: any`
  - `b: any`
- **Return Type**: `number`
- **Calls**:
  - `String(a.key).localeCompare`
### `sortMapEntries(a: any, b: any): number`

<details><summary>Code</summary>

```ts
(a, b) => String(a.key).localeCompare(String(b.key))
```
</details>

- **Parameters**:
  - `a: any`
  - `b: any`
- **Return Type**: `number`
- **Calls**:
  - `String(a.key).localeCompare`

---