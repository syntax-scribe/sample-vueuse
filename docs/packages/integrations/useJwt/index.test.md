[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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

## 🔧 Functions

> No functions found in this file.


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