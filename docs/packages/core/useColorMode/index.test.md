[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 12 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `storageKey` | `"vueuse-color-scheme"` | const | `'vueuse-color-scheme'` | ✗ |
| `mockPreferredDark` | `Ref<boolean>` | const | `usePreferredDark() as Ref<boolean>` | ✗ |
| `nextMode` | `any` | let/var | `null` | ✗ |


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