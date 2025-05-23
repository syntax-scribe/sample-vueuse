[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 8
- **Classes**: 0
- **Imports**: 16
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useStorage/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `debounceFilter` | `@vueuse/shared` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `defineComponent` | `vue` |
| `nextTick` | `vue` |
| `toRaw` | `vue` |
| `mount` | `../../.test` |
| `nextTwoTick` | `../../.test` |
| `useSetup` | `../../.test` |
| `customStorageEventName` | `./index` |
| `StorageSerializers` | `./index` |
| `useStorage` | `./index` |


---

## Functions

### `mergeDefaults(value: string, initial: string): string[]`

<details><summary>Code</summary>

```ts
(value, initial) => [...initial, ...value]
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string[]`
### `mergeDefaults(value: string, initial: string): string[]`

<details><summary>Code</summary>

```ts
(value, initial) => [...initial, ...value]
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string[]`
### `mergeDefaults(value: string, initial: string): string`

<details><summary>Code</summary>

```ts
(value, initial) => value + initial
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string`
### `mergeDefaults(value: string, initial: string): string`

<details><summary>Code</summary>

```ts
(value, initial) => value + initial
```
</details>

- **Parameters**:
  - `value: string`
  - `initial: string`
- **Return Type**: `string`
### `getItem(): any`

<details><summary>Code</summary>

```ts
() => null
```
</details>

- **Return Type**: `any`
### `setItem(): never`

<details><summary>Code</summary>

```ts
() => { throw new Error('write item error') }
```
</details>

- **Return Type**: `never`
### `getItem(): any`

<details><summary>Code</summary>

```ts
() => null
```
</details>

- **Return Type**: `any`
### `setItem(): never`

<details><summary>Code</summary>

```ts
() => { throw new Error('write item error') }
```
</details>

- **Return Type**: `never`

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