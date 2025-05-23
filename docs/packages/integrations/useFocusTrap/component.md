[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 1
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---