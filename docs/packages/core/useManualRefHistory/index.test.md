[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useManualRefHistory/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `deepRef` | `vue` |
| `isReactive` | `vue` |
| `shallowRef` | `vue` |
| `useManualRefHistory` | `./index` |


---

## Functions

### `clone(x: unknown): any`

<details><summary>Code</summary>

```ts
x => JSON.parse(JSON.stringify(x))
```
</details>

- **Parameters**:
  - `x: unknown`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `clone(x: unknown): any`

<details><summary>Code</summary>

```ts
x => JSON.parse(JSON.stringify(x))
```
</details>

- **Parameters**:
  - `x: unknown`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `dump(v: any): string`

<details><summary>Code</summary>

```ts
v => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `parse(v: string): any`

<details><summary>Code</summary>

```ts
(v: string) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `dump(v: any): string`

<details><summary>Code</summary>

```ts
v => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `parse(v: string): any`

<details><summary>Code</summary>

```ts
(v: string) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: string`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`

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