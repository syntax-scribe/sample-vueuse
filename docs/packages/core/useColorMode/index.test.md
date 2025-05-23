[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 12
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useColorMode/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `afterAll` | `vitest` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `nextTwoTick` | `../../.test` |
| `usePreferredDark` | `../usePreferredDark` |
| `useColorMode` | `./index` |


---

## Functions

### `usePreferredDark(): any`

<details><summary>Code</summary>

```ts
() => mockPreferredDark
```
</details>

- **Return Type**: `any`
### `usePreferredDark(): any`

<details><summary>Code</summary>

```ts
() => mockPreferredDark
```
</details>

- **Return Type**: `any`
### `onChanged(mode: any, defaultOnChanged: any): void`

<details><summary>Code</summary>

```ts
(mode: any, defaultOnChanged: any) => {
      nextMode = mode
      defaultOnChanged(mode)
    }
```
</details>

- **Parameters**:
  - `mode: any`
  - `defaultOnChanged: any`
- **Return Type**: `void`
- **Calls**:
  - `defaultOnChanged`

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