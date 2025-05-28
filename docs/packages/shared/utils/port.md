[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `port.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 0 |
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

- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/utils/port.ts`**

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `hit` | `string` | const | `cache[str]` | ✗ |
| `hyphenateRE` | `RegExp` | const | `/\B([A-Z])/g` | ✗ |
| `camelizeRE` | `RegExp` | const | `/-(\w)/g` | ✗ |


---

## Functions

### `cacheStringFunction(fn: T): T`

<details><summary>Code</summary>

```ts
function cacheStringFunction<T extends (str: string) => string>(fn: T): T {
  const cache: Record<string, string> = Object.create(null)
  return ((str: string) => {
    const hit = cache[str]
    return hit || (cache[str] = fn(str))
  }) as T
}
```
</details>

- **Parameters**:
  - `fn: T`
- **Return Type**: `T`
- **Calls**:
  - `Object.create`
  - `fn`

---