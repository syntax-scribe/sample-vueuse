[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/useToString/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `useToString(value: MaybeRefOrGetter<unknown>): ComputedRef<string>`

<details><summary>Code</summary>

```ts
export function useToString(
  value: MaybeRefOrGetter<unknown>,
): ComputedRef<string> {
  return computed(() => `${toValue(value)}`)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively convert a ref to string.
 *
 * @see https://vueuse.org/useToString
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<unknown>`
- **Return Type**: `ComputedRef<string>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`

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