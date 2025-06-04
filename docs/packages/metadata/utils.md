[⬅️ Back to Table of Contents](../../index.md)

# 📄 `utils.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/metadata/utils.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `VueUseFunction` | `./types` |


---

## Functions

### `getCategories(functions: VueUseFunction[]): string[]`

<details><summary>Code</summary>

```ts
export function getCategories(functions: VueUseFunction[]): string[] {
  return uniq(
    functions
      .filter(i => !i.internal)
      .map(i => i.category)
      .filter(Boolean),
  ).sort(
    (a, b) => (a.startsWith('@') && !b.startsWith('@'))
      ? 1
      : (b.startsWith('@') && !a.startsWith('@'))
          ? -1
          : a.localeCompare(b),
  )
}
```
</details>

- **Parameters**:
  - `functions: VueUseFunction[]`
- **Return Type**: `string[]`
- **Calls**:
  - `uniq(
    functions
      .filter(i => !i.internal)
      .map(i => i.category)
      .filter(Boolean),
  ).sort`
  - `a.startsWith`
  - `b.startsWith`
  - `a.localeCompare`
### `uniq(a: T): any[]`

<details><summary>Code</summary>

```ts
export function uniq<T extends any[]>(a: T) {
  return Array.from(new Set(a))
}
```
</details>

- **Parameters**:
  - `a: T`
- **Return Type**: `any[]`
- **Calls**:
  - `Array.from`

---