[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 📦 Imports | 9 |
| 📐 Interfaces | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)

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