[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 12
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useDraggable/component.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseDraggableOptions` | `@vueuse/core` |
| `Position` | `../types` |
| `RenderableComponent` | `../types` |
| `isClient` | `@vueuse/core` |
| `useDraggable` | `@vueuse/core` |
| `useStorage` | `@vueuse/core` |
| `computed` | `vue` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `onEnd(position: Position, event: PointerEvent): void`

<details><summary>Code</summary>

```ts
(position: Position, event: PointerEvent) => {
      props.onEnd?.(position, event)
      if (!storageValue)
        return
      storageValue.value.x = position.x
      storageValue.value.y = position.y
    }
```
</details>

- **Parameters**:
  - `position: Position`
  - `event: PointerEvent`
- **Return Type**: `void`
- **Calls**:
  - `props.onEnd`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseDraggableProps`

<details><summary>Interface Code</summary>

```ts
export interface UseDraggableProps extends UseDraggableOptions, RenderableComponent {
  /**
   * When provided, use `useStorage` to preserve element's position
   */
  storageKey?: string

  /**
   * Storage type
   *
   * @default 'local'
   */
  storageType?: 'local' | 'session'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `storageKey` | `string` | ✓ |  |
| `storageType` | `'local' | 'session'` | ✓ |  |


---

## Type Aliases

> No type aliases found in this file.


---