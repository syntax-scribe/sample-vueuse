[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 2 |
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
📂 **`packages/core/useNow/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `useNow` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `initial` | `number` | const | `+new Date()` | ✗ |
| `initial` | `number` | let/var | `+new Date()` | ✗ |


---

## Functions

### `testControl(interval: any): void`

<details><summary>Code</summary>

```ts
function testControl(interval: any) {
    it(`should control now timestamp by ${interval}`, async () => {
      let initial = +new Date()
      const { now, pause, resume } = useNow({ controls: true, interval })

      expect(+now.value).toBeGreaterThanOrEqual(initial)

      vi.advanceTimersByTime(50)

      expect(+now.value).toBeGreaterThan(initial)

      initial = +now.value

      pause()
      vi.advanceTimersByTime(50)

      expect(+now.value).toBe(initial)

      resume()
      vi.advanceTimersByTime(50)

      expect(+now.value).toBeGreaterThan(initial)
    })
  }
```
</details>

- **Parameters**:
  - `interval: any`
- **Return Type**: `void`
- **Calls**:
  - `it (from vitest)`
  - `useNow (from ./index)`
  - `expect(+now.value).toBeGreaterThanOrEqual`
  - `vi.advanceTimersByTime`
  - `expect(+now.value).toBeGreaterThan`
  - `pause`
  - `expect(+now.value).toBe`
  - `resume`

---