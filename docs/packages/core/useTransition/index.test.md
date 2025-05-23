[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 0
- **Type Aliases**: 0

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