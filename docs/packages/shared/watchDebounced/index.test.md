[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 8 |
| ⚡ Async/Await Patterns | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

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

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `constantUpdateOverTime` | vi.advanceTimersByTimeAsync(1) | *none* |


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