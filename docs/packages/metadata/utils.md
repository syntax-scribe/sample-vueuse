[⬅️ Back to Table of Contents](../../index.md)

# 📄 `utils.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 1
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---