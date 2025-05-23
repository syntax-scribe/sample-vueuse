[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/watchDebounced/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `debouncedWatch` | `./index` |
| `watchDebounced` | `./index` |


---

## Functions

### `constantUpdateOverTime(ms: number): Promise<void>`

<details><summary>Code</summary>

```ts
async (ms: number) => {
      for (let i = 0; i < ms; i++) {
        num.value += 1
        await vi.advanceTimersByTimeAsync(1)
      }
    }
```
</details>

- **Parameters**:
  - `ms: number`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `vi.advanceTimersByTimeAsync`

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