[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/onLongPress/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `onLongPress` | `@vueuse/core` |
| `shallowRef` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---