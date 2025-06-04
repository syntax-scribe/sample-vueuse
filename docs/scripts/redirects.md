[⬅️ Back to Table of Contents](../index.md)

# 📄 `redirects.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 1 |
| ⚡ Async/Await Patterns | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`scripts/redirects.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `functions` | `../packages/metadata/metadata` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `buildRedirects` | fs.writeFile('packages/.vitepress/dist/_redirects', redirects, 'utf-8') | *none* |


---

## Functions

### `buildRedirects(): Promise<void>`

<details><summary>Code</summary>

```ts
async function buildRedirects() {
  const redirects = functions
    .filter(f => f.docs && !f.internal && !f.deprecated)
    .flatMap(f => ([f.name, ...f.alias || []]).map(n => `/${n}\t${f.docs}\t302`))
    .join('\n')

  await fs.writeFile('packages/.vitepress/dist/_redirects', redirects, 'utf-8')
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `functions
    .filter(f => f.docs && !f.internal && !f.deprecated)
    .flatMap(f => ([f.name, ...f.alias || []]).map(n => `/${n}\t${f.docs}\t302`))
    .join`
  - `fs.writeFile`

---