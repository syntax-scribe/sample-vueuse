[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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