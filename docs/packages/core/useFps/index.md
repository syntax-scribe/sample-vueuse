[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useFps/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `shallowRef` | `vue` |
| `useRafFn` | `../useRafFn` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `every` | `number` | const | `options?.every ?? 10` | ✗ |
| `ticks` | `number` | let/var | `0` | ✗ |
| `diff` | `number` | const | `now - last` | ✗ |


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