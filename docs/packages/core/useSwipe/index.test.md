[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `threshold` | `30` | const | `30` | ✗ |
| `onSwipe` | `any` | let/var | `*not shown*` | ✗ |
| `onSwipeEnd` | `any` | let/var | `*not shown*` | ✗ |


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