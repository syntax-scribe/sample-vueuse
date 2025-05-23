[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `guess.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useStorage/guess.ts`**

## 📦 Imports

> No imports found in this file.


---

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---