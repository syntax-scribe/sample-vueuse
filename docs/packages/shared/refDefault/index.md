[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/refDefault/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `computed` | `vue` |


---

## Functions

### `refDefault(source: Ref<T | undefined | null>, defaultValue: T): Ref<T>`

<details><summary>Code</summary>

```ts
export function refDefault<T>(source: Ref<T | undefined | null>, defaultValue: T): Ref<T> {
  return computed({
    get() {
      return source.value ?? defaultValue
    },
    set(value) {
      source.value = value
    },
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Apply default value to a ref.
 */
```

- **Parameters**:
  - `source: Ref<T | undefined | null>`
  - `defaultValue: T`
- **Return Type**: `Ref<T>`
- **Calls**:
  - `computed (from vue)`

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