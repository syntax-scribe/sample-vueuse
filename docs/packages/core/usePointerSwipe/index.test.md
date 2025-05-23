[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/usePointerSwipe/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UsePointerSwipeOptions` | `./index` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `usePointerSwipe` | `./index` |


---

## Functions

### `mockPointerEventInit(x: number, y: number): PointerEventInit`

<details><summary>Code</summary>

```ts
function mockPointerEventInit(x: number, y: number): PointerEventInit {
  return {
    clientX: x,
    clientY: y,
  }
}
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `PointerEventInit`
### `mockPointerDown(x: number, y: number): PointerEvent`

<details><summary>Code</summary>

```ts
function mockPointerDown(x: number, y: number) {
  return new PointerEvent('pointerdown', mockPointerEventInit(x, y))
}
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `PointerEvent`
- **Calls**:
  - `mockPointerEventInit`
### `mockPointerMove(x: number, y: number): PointerEvent`

<details><summary>Code</summary>

```ts
function mockPointerMove(x: number, y: number) {
  return new PointerEvent('pointermove', mockPointerEventInit(x, y))
}
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `PointerEvent`
- **Calls**:
  - `mockPointerEventInit`
### `mockPointerUp(x: number, y: number): PointerEvent`

<details><summary>Code</summary>

```ts
function mockPointerUp(x: number, y: number) {
  return new PointerEvent('pointerup', mockPointerEventInit(x, y))
}
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `PointerEvent`
- **Calls**:
  - `mockPointerEventInit`
### `mockPointerEvents(target: Element, coords: Array<number[]>): void`

<details><summary>Code</summary>

```ts
function mockPointerEvents(target: Element, coords: Array<number[]>) {
  coords.forEach(([x, y], i) => {
    if (i === 0)
      target.dispatchEvent(mockPointerDown(x, y))
    else if (i === coords.length - 1)
      target.dispatchEvent(mockPointerUp(x, y))
    else
      target.dispatchEvent(mockPointerMove(x, y))
  })
}
```
</details>

- **Parameters**:
  - `target: Element`
  - `coords: Array<number[]>`
- **Return Type**: `void`
- **Calls**:
  - `coords.forEach`
  - `target.dispatchEvent`
  - `mockPointerDown`
  - `mockPointerUp`
  - `mockPointerMove`
### `options(): UsePointerSwipeOptions`

<details><summary>Code</summary>

```ts
(): UsePointerSwipeOptions => ({
    threshold,
    onSwipeStart,
    onSwipe,
    onSwipeEnd,
  })
```
</details>

- **Return Type**: `UsePointerSwipeOptions`

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