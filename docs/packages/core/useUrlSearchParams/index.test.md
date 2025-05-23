[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useUrlSearchParams/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `useUrlSearchParams` | `./index` |


---

## Functions

### `mockPopstate(search: string, hash: string): void`

<details><summary>Code</summary>

```ts
(search: string, hash: string) => {
    window.location.search = search
    window.location.hash = hash
    window.dispatchEvent(new PopStateEvent('popstate', {
      state: {
        ...window.location,
        search,
        hash,
      },
    }))
  }
```
</details>

- **Parameters**:
  - `search: string`
  - `hash: string`
- **Return Type**: `void`
- **Calls**:
  - `window.dispatchEvent`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `CustomUrlParams`

<details><summary>Interface Code</summary>

```ts
interface CustomUrlParams extends Record<string, any> {
          customFoo: number | undefined
        }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `customFoo` | `number | undefined` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---