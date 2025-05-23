[⬅️ Back to Table of Contents](../index.md)

# 📄 `contributors.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 1
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/contributors.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `contributorsGenerated` | `./contributors.json` |


---

## Functions

### `getAvatarUrl(name: string): string`

<details><summary>Code</summary>

```ts
function getAvatarUrl(name: string) {
  return `https://avatars.githubusercontent.com/${name}?v=4`
}
```
</details>

- **Parameters**:
  - `name: string`
- **Return Type**: `string`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `Contributor`

<details><summary>Interface Code</summary>

```ts
export interface Contributor {
  name: string
  avatar: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `name` | `string` | ✗ |  |
| `avatar` | `string` | ✗ |  |

### `TeamMember`

<details><summary>Interface Code</summary>

```ts
export interface TeamMember {
  avatar: string
  name: string
  github: string
  twitter?: string
  bluesky?: string
  sponsors?: boolean
  description: string
  packages?: string[]
  functions?: string[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `avatar` | `string` | ✗ |  |
| `name` | `string` | ✗ |  |
| `github` | `string` | ✗ |  |
| `twitter` | `string` | ✓ |  |
| `bluesky` | `string` | ✓ |  |
| `sponsors` | `boolean` | ✓ |  |
| `description` | `string` | ✗ |  |
| `packages` | `string[]` | ✓ |  |
| `functions` | `string[]` | ✓ |  |


---

## Type Aliases

> No type aliases found in this file.


---