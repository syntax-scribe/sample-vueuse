[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.browser.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useElementBounding/index.browser.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `page` | `@vitest/browser/context` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `computed` | `vue` |
| `defineComponent` | `vue` |
| `shallowRef` | `vue` |
| `useElementBounding` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `content` | `any` | let/var | `pre.query()?.textContent` | ✗ |
| `contentBefore` | `any` | let/var | `pre.query()?.textContent` | ✗ |
| `contentAfterFirstUpdate` | `any` | let/var | `pre.query()?.textContent` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `handleWidth(): void`

<details><summary>Code</summary>

```ts
() => {
      width.value = '34px'
    }
```
</details>

- **Return Type**: `void`
### `handleMargin(): void`

<details><summary>Code</summary>

```ts
() => {
      margin.value = '69px'
    }
```
</details>

- **Return Type**: `void`
### `handleRemove(): void`

<details><summary>Code</summary>

```ts
() => {
      hasElement.value = false
    }
```
</details>

- **Return Type**: `void`

---