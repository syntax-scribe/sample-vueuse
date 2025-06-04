[⬅️ Back to Table of Contents](../../index.md)

# 📄 `types.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔄 Re-exports | 1 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Re-exports](#re-exports)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/types.ts`**

## Re-exports

| Type | Source | Exported Names |
|------|--------|----------------|
| namespace | `./_configurable` | * |


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