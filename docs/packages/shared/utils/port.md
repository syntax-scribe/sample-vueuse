[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `port.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/utils/port.ts`**

## 📦 Imports

> No imports found in this file.


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---