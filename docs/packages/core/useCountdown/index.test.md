[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---