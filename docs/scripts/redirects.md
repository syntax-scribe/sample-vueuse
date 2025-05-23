[⬅️ Back to Table of Contents](../index.md)

# 📄 `redirects.ts`

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
📂 **`scripts/redirects.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `functions` | `../packages/metadata/metadata` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---