[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 5 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useSorted/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `toValue` | `vue` |
| `useSorted` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `arr` | `number[]` | const | `[10, 3, 5, 7, 2, 1, 8, 6, 9, 4]` | ✗ |
| `arrSorted` | `number[]` | const | `[1, 2, 3, 4, 5, 6, 7, 8, 9, 10]` | ✗ |
| `objArr` | `User[]` | const | `[
  {
    name: 'John',
    age: 40,
  },
  {
    name: 'Jane',
    age: 20,
  },
  {
    name: 'Joe',
    age: 30,
  },
  {
    name: 'Jenny',
    age: 22,
  },
]` | ✗ |
| `objectSorted` | `User[]` | const | `[
  {
    name: 'Jane',
    age: 20,
  },
  {
    name: 'Jenny',
    age: 22,
  },
  {
    name: 'Joe',
    age: 30,
  },
  {
    name: 'John',
    age: 40,
  },
]` | ✗ |
| `dirtyArr` | `number[]` | const | `[...arr]` | ✗ |


---

## Functions

### `compareFn(a: any, b: any): number`

<details><summary>Code</summary>

```ts
(a, b) => a.age - b.age
```
</details>

- **Parameters**:
  - `a: any`
  - `b: any`
- **Return Type**: `number`
### `compareFn(a: any, b: any): number`

<details><summary>Code</summary>

```ts
(a, b) => a.age - b.age
```
</details>

- **Parameters**:
  - `a: any`
  - `b: any`
- **Return Type**: `number`
### `compareFn(a: any, b: any): number`

<details><summary>Code</summary>

```ts
(a, b) => a.age - b.age
```
</details>

- **Parameters**:
  - `a: any`
  - `b: any`
- **Return Type**: `number`
### `compareFn(a: any, b: any): number`

<details><summary>Code</summary>

```ts
(a, b) => a.age - b.age
```
</details>

- **Parameters**:
  - `a: any`
  - `b: any`
- **Return Type**: `number`

---

## Interfaces

### `User`

<details><summary>Interface Code</summary>

```ts
interface User {
  name: string
  age: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `name` | `string` | ✗ |  |
| `age` | `number` | ✗ |  |


---