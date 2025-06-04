[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 7 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `threshold` | `30` | const | `30` | ✗ |
| `onSwipeStart` | `any` | let/var | `*not shown*` | ✗ |
| `onSwipe` | `any` | let/var | `*not shown*` | ✗ |
| `onSwipeEnd` | `any` | let/var | `*not shown*` | ✗ |
| `directionTests` | `(string | number[][])[][]` | const | `[
    ['up', [[0, 2 * threshold], [0, threshold], [0, threshold]]],
    ['down', [[0, 0], [0, threshold], [0, threshold]]],
    ['left', [[2 * threshold, 0], [threshold, 0], [threshold, 0]]],
    ['right', [[0, 0], [threshold, 0], [threshold, 0]]],
  ]` | ✗ |
| `_direction` | `string | number[][]` | const | `config[0]` | ✗ |
| `coords` | `number[][]` | const | `config[1] as unknown as number[][]` | ✗ |


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