[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 2 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/useIntervalFn/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `../utils` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `effectScope` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `useIntervalFn` | `./index` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `exec` | vi.advanceTimersByTimeAsync(60), vi.advanceTimersByTimeAsync(60), vi.advanceTimersByTimeAsync(60) | *none* |
| async-function | `execImmediateCallback` | vi.advanceTimersByTimeAsync(60), vi.advanceTimersByTimeAsync(60), vi.advanceTimersByTimeAsync(60) | *none* |


---

## Functions

### `exec({ isActive, pause, resume }: Pausable): Promise<void>`

<details><summary>Code</summary>

```ts
async function exec({ isActive, pause, resume }: Pausable) {
    expect(isActive.value).toBeTruthy()
    expect(callback).toHaveBeenCalledTimes(0)

    await vi.advanceTimersByTimeAsync(60)
    expect(callback).toHaveBeenCalledTimes(1)

    pause()
    expect(isActive.value).toBeFalsy()

    await vi.advanceTimersByTimeAsync(60)
    expect(callback).toHaveBeenCalledTimes(1)

    resume()
    expect(isActive.value).toBeTruthy()

    await vi.advanceTimersByTimeAsync(60)
    expect(callback).toHaveBeenCalledTimes(2)
  }
```
</details>

- **Parameters**:
  - `{ isActive, pause, resume }: Pausable`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `expect(isActive.value).toBeTruthy`
  - `expect(callback).toHaveBeenCalledTimes`
  - `vi.advanceTimersByTimeAsync`
  - `pause`
  - `expect(isActive.value).toBeFalsy`
  - `resume`
### `execImmediateCallback({ isActive, pause, resume }: Pausable): Promise<void>`

<details><summary>Code</summary>

```ts
async function execImmediateCallback({ isActive, pause, resume }: Pausable) {
    expect(isActive.value).toBeTruthy()
    expect(callback).toHaveBeenCalledTimes(1)

    await vi.advanceTimersByTimeAsync(60)
    expect(callback).toHaveBeenCalledTimes(2)

    pause()
    expect(isActive.value).toBeFalsy()

    await vi.advanceTimersByTimeAsync(60)
    expect(callback).toHaveBeenCalledTimes(2)

    resume()
    expect(isActive.value).toBeTruthy()
    expect(callback).toHaveBeenCalledTimes(3)

    await vi.advanceTimersByTimeAsync(60)
    expect(callback).toHaveBeenCalledTimes(4)
  }
```
</details>

- **Parameters**:
  - `{ isActive, pause, resume }: Pausable`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `expect(isActive.value).toBeTruthy`
  - `expect(callback).toHaveBeenCalledTimes`
  - `vi.advanceTimersByTimeAsync`
  - `pause`
  - `expect(isActive.value).toBeFalsy`
  - `resume`

---