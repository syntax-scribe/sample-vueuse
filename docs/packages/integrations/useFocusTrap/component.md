[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/integrations/useFocusTrap/component.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `RenderableComponent` | `@vueuse/core` |
| `FocusTrap` | `focus-trap` |
| `UseFocusTrapOptions` | `./index` |
| `unrefElement` | `@vueuse/core` |
| `createFocusTrap` | `focus-trap` |
| `deepRef` | `vue` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `onScopeDispose` | `vue` |
| `watch` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `trap` | `undefined | FocusTrap` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `activate(): any`

<details><summary>Code</summary>

```ts
() => trap && trap.activate()
```
</details>

- **Return Type**: `any`
### `deactivate(): any`

<details><summary>Code</summary>

```ts
() => trap && trap.deactivate()
```
</details>

- **Return Type**: `any`

---

## Interfaces

### `ComponentUseFocusTrapOptions`

<details><summary>Interface Code</summary>

```ts
export interface ComponentUseFocusTrapOptions extends RenderableComponent {
  options?: UseFocusTrapOptions
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `options` | `UseFocusTrapOptions` | ✓ |  |


---