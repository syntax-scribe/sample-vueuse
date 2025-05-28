[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `guess.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 0 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useStorage/guess.ts`**

## Functions

### `guessSerializerType(rawInit: T): "any" | "set" | "map" | "date" | "boolean" | "string" | "object" | "number"`

<details><summary>Code</summary>

```ts
export function guessSerializerType<T extends(string | number | boolean | object | null)>(rawInit: T) {
  return rawInit == null
    ? 'any'
    : rawInit instanceof Set
      ? 'set'
      : rawInit instanceof Map
        ? 'map'
        : rawInit instanceof Date
          ? 'date'
          : typeof rawInit === 'boolean'
            ? 'boolean'
            : typeof rawInit === 'string'
              ? 'string'
              : typeof rawInit === 'object'
                ? 'object'
                : !Number.isNaN(rawInit)
                    ? 'number'
                    : 'any'
}
```
</details>

- **Parameters**:
  - `rawInit: T`
- **Return Type**: `"any" | "set" | "map" | "date" | "boolean" | "string" | "object" | "number"`
- **Calls**:
  - `Number.isNaN`

---