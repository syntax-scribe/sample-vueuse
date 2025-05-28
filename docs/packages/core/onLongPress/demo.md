[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
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
📂 **`packages/core/onLongPress/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `onLongPress` | `@vueuse/core` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `htmlRef` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |
| `htmlRefOptions` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |
| `htmlRefOnMouseUp` | `number` | let/var | `shallowRef<HTMLElement | null>(null)` | ✗ |


---

## Functions

### `onLongPressCallback(e: PointerEvent): void`

<details><summary>Code</summary>

```ts
function onLongPressCallback(e: PointerEvent) {
  longPressed.value = true
}
```
</details>

- **Parameters**:
  - `e: PointerEvent`
- **Return Type**: `void`
### `onMouseUpCallback(duration: number, distance: number, isLongPress: boolean): void`

<details><summary>Code</summary>

```ts
function onMouseUpCallback(duration: number, distance: number, isLongPress: boolean) {
  if (!isLongPress)
    clicked.value = true

  console.log({ distance, duration, isLongPress })
}
```
</details>

- **Parameters**:
  - `duration: number`
  - `distance: number`
  - `isLongPress: boolean`
- **Return Type**: `void`
- **Calls**:
  - `console.log`
### `reset(): void`

<details><summary>Code</summary>

```ts
function reset() {
  longPressed.value = false
  clicked.value = false
}
```
</details>

- **Return Type**: `void`

---