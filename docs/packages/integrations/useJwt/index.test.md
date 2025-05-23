[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/integrations/useJwt/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `JwtHeader` | `jwt-decode` |
| `JwtPayload` | `jwt-decode` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `useJwt` | `./index` |


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


---

## Interfaces

### `CustomJwtHeader`

<details><summary>Interface Code</summary>

```ts
interface CustomJwtHeader extends JwtHeader {
  foo: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `foo` | `string` | ✗ |  |

### `CustomJwtPayload`

<details><summary>Interface Code</summary>

```ts
interface CustomJwtPayload extends JwtPayload {
  foo: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `foo` | `string` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---