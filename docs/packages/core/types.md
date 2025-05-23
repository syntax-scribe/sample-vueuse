[⬅️ Back to Table of Contents](../../index.md)

# 📄 `types.ts`

## 📚 Table of Contents

- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/types.ts`**

## 📦 Imports

> No imports found in this file.


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


---

## Interfaces

### `Position`

<details><summary>Interface Code</summary>

```ts
export interface Position {
  x: number
  y: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `x` | `number` | ✗ |  |
| `y` | `number` | ✗ |  |

### `RenderableComponent`

<details><summary>Interface Code</summary>

```ts
export interface RenderableComponent {
  /**
   * The element that the component should be rendered as
   *
   * @default 'div'
   */
  as?: object | string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `as` | `object | string` | ✓ |  |


---

## Type Aliases

### `PointerType`

```ts
type PointerType = 'mouse' | 'touch' | 'pen';
```


---