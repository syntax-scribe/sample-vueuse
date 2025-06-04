[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `guess.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |

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