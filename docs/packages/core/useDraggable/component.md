[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `component.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 12 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 4 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `storageValue` | `any` | const | `props.storageKey && useStorage(
      props.storageKey,
      toValue(props.initialValue) || { x: 0, y: 0 },
      isClient
        ? props.storageType === 'session'
          ? sessionStorage
          : localStorage
        : undefined,
    )` | ✗ |
| `initialValue` | `any` | const | `storageValue || props.initialValue || { x: 0, y: 0 }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `reactive` | reactive | *none* | *none* |


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