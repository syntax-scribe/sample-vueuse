[⬅️ Back to Table of Contents](../index.md)

# 📄 `update.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 1 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

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

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `run` | Promise.all([
    updateImport(metadata),
    updatePackageREADME(metadata),
    updateIndexREADME(metadata),
    updateFunctionsMD(metadata),
    updateFunctionREADME(metadata),
    updatePackageJSON(metadata),
    updateCountBadge(metadata),
    process.env.NETLIFY && updateContributors(),
  ]), fs.copyFile('./CONTRIBUTING.md', './packages/contributing.md') | Promise.all |


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