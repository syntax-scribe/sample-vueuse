[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useFps/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `shallowRef` | `vue` |
| `useRafFn` | `../useRafFn` |


---

## Functions

### `useFps(options: UseFpsOptions): ShallowRef<number>`

<details><summary>Code</summary>

```ts
export function useFps(options?: UseFpsOptions): ShallowRef<number> {
  const fps = shallowRef(0)
  if (typeof performance === 'undefined')
    return fps
  const every = options?.every ?? 10

  let last = performance.now()
  let ticks = 0

  useRafFn(() => {
    ticks += 1
    if (ticks >= every) {
      const now = performance.now()
      const diff = now - last
      fps.value = Math.round(1000 / (diff / ticks))
      last = now
      ticks = 0
    }
  })

  return fps
}
```
</details>

- **Parameters**:
  - `options: UseFpsOptions`
- **Return Type**: `ShallowRef<number>`
- **Calls**:
  - `shallowRef (from vue)`
  - `performance.now`
  - `useRafFn (from ../useRafFn)`
  - `Math.round`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseFpsOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFpsOptions {
  /**
   * Calculate the FPS on every x frames.
   * @default 10
   */
  every?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `every` | `number` | ✓ |  |


---

## Type Aliases

> No type aliases found in this file.


---