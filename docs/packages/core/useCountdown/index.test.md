[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 1 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useCountdown/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `UseCountdownOptions` | `./index` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `effectScope` | `vue` |
| `shallowRef` | `vue` |
| `useCountdown` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `countdown` | `number` | let/var | `3` | ✗ |
| `interval` | `number` | let/var | `100` | ✗ |
| `immediate` | `true` | const | `true` | ✗ |
| `options` | `UseCountdownOptions` | let/var | `{
    interval,
    onComplete: completeCallback,
    onTick: tickCallback,
    immediate,
  }` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `exec` | *none* | *none* |


---

## Functions

### `exec({ isActive, pause, resume }: Pausable): Promise<void>`

<details><summary>Code</summary>

```ts
async function exec({ isActive, pause, resume }: Pausable) {
    expect(isActive.value).toBeTruthy()
    expect(completeCallback).toHaveBeenCalledTimes(0)
    vi.advanceTimersByTime(110)
    expect(tickCallback).toHaveBeenCalledTimes(1)

    pause()
    expect(isActive.value).toBeFalsy()

    vi.advanceTimersByTime(110)
    expect(tickCallback).toHaveBeenCalledTimes(1)

    resume()
    expect(isActive.value).toBeTruthy()

    vi.advanceTimersByTime(110)
    expect(tickCallback).toHaveBeenCalledTimes(2)

    vi.advanceTimersByTime(110)
    expect(tickCallback).toHaveBeenCalledTimes(3)
    expect(completeCallback).toHaveBeenCalledTimes(1)
  }
```
</details>

- **Parameters**:
  - `{ isActive, pause, resume }: Pausable`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `expect(isActive.value).toBeTruthy`
  - `expect(completeCallback).toHaveBeenCalledTimes`
  - `vi.advanceTimersByTime`
  - `expect(tickCallback).toHaveBeenCalledTimes`
  - `pause`
  - `expect(isActive.value).toBeFalsy`
  - `resume`

---