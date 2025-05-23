[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 5
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useSwipe/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useSwipe` | `./index` |


---

## Functions

### `mockTouchEventInit(x: number, y: number): TouchEventInit`

<details><summary>Code</summary>

```ts
(x: number, y: number): TouchEventInit => ({
    touches: [{
      clientX: x,
      clientY: y,
      force: 0,
      identifier: 0,
      pageX: 0,
      pageY: 0,
      radiusX: 0,
      radiusY: 0,
      rotationAngle: 0,
      screenX: 0,
      screenY: 0,
      target,
    }],
  })
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `TouchEventInit`
### `mockTouchStart(x: number, y: number): TouchEvent`

<details><summary>Code</summary>

```ts
(x: number, y: number) => new TouchEvent('touchstart', mockTouchEventInit(x, y))
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `TouchEvent`
### `mockTouchMove(x: number, y: number): TouchEvent`

<details><summary>Code</summary>

```ts
(x: number, y: number) => new TouchEvent('touchmove', mockTouchEventInit(x, y))
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `TouchEvent`
### `mockTouchEnd(x: number, y: number): TouchEvent`

<details><summary>Code</summary>

```ts
(x: number, y: number) => new TouchEvent('touchend', mockTouchEventInit(x, y))
```
</details>

- **Parameters**:
  - `x: number`
  - `y: number`
- **Return Type**: `TouchEvent`
### `mockTouchEvents(target: EventTarget, coords: Array<number[]>): void`

<details><summary>Code</summary>

```ts
(target: EventTarget, coords: Array<number[]>) => {
    coords.forEach(([x, y], i) => {
      if (i === 0)
        target.dispatchEvent(mockTouchStart(x, y))
      else if (i === coords.length - 1)
        target.dispatchEvent(mockTouchEnd(x, y))
      else
        target.dispatchEvent(mockTouchMove(x, y))
    })
  }
```
</details>

- **Parameters**:
  - `target: EventTarget`
  - `coords: Array<number[]>`
- **Return Type**: `void`
- **Calls**:
  - `coords.forEach`
  - `target.dispatchEvent`
  - `mockTouchStart`
  - `mockTouchEnd`
  - `mockTouchMove`

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