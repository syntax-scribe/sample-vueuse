[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 3 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `baseURL` | `"https://vueuse.org"` | const | `'https://vueuse.org'` | ✗ |
| `initialValue` | `{ foo: string; }` | let/var | `{ foo: 'bar' }` | ✗ |
| `newHash` | `"#/change/?foo=bar"` | const | `'#/change/?foo=bar'` | ✗ |


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