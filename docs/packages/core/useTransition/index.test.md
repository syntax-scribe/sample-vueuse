[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useTransition/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `promiseTimeout` | `@vueuse/shared` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `executeTransition` | `./index` |
| `useTransition` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `abort` | `boolean` | let/var | `false` | ✗ |


---

## Functions

### `expectBetween(val: number, floor: number, ceiling: number): void`

<details><summary>Code</summary>

```ts
function expectBetween(val: number, floor: number, ceiling: number) {
  expect(val).to.be.greaterThan(floor)
  expect(val).to.be.lessThan(ceiling)
}
```
</details>

- **Parameters**:
  - `val: number`
  - `floor: number`
  - `ceiling: number`
- **Return Type**: `void`
- **Calls**:
  - `expect(val).to.be.greaterThan`
  - `expect(val).to.be.lessThan`
### `abort(): boolean`

<details><summary>Code</summary>

```ts
() => abort
```
</details>

- **Return Type**: `boolean`
### `abort(): boolean`

<details><summary>Code</summary>

```ts
() => abort
```
</details>

- **Return Type**: `boolean`
### `abort(): boolean`

<details><summary>Code</summary>

```ts
() => abort
```
</details>

- **Return Type**: `boolean`
### `abort(): boolean`

<details><summary>Code</summary>

```ts
() => abort
```
</details>

- **Return Type**: `boolean`

---