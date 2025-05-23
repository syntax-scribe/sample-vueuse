[⬅️ Back to Table of Contents](../index.md)

# 📄 `update.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`scripts/update.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `process` | `node:process` |
| `metadata` | `../packages/metadata/metadata` |
| `updateContributors` | `./utils` |
| `updateCountBadge` | `./utils` |
| `updateFunctionREADME` | `./utils` |
| `updateFunctionsMD` | `./utils` |
| `updateImport` | `./utils` |
| `updateIndexREADME` | `./utils` |
| `updatePackageJSON` | `./utils` |
| `updatePackageREADME` | `./utils` |


---

## Functions

### `run(): Promise<void>`

<details><summary>Code</summary>

```ts
async function run() {
  await Promise.all([
    updateImport(metadata),
    updatePackageREADME(metadata),
    updateIndexREADME(metadata),
    updateFunctionsMD(metadata),
    updateFunctionREADME(metadata),
    updatePackageJSON(metadata),
    updateCountBadge(metadata),
    process.env.NETLIFY && updateContributors(),
  ])

  await fs.copyFile('./CONTRIBUTING.md', './packages/contributing.md')
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `Promise.all`
  - `updateImport (from ./utils)`
  - `updatePackageREADME (from ./utils)`
  - `updateIndexREADME (from ./utils)`
  - `updateFunctionsMD (from ./utils)`
  - `updateFunctionREADME (from ./utils)`
  - `updatePackageJSON (from ./utils)`
  - `updateCountBadge (from ./utils)`
  - `updateContributors (from ./utils)`
  - `fs.copyFile`

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