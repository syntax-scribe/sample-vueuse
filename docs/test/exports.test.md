[⬅️ Back to Table of Contents](../index.md)

# 📄 `exports.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
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