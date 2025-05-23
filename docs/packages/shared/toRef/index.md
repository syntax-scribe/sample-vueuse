[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/toRef/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `ToRef` | `vue` |
| `customRef` | `vue` |
| `deepRef` | `vue` |
| `readonly` | `vue` |
| `vueToRef` | `vue` |
| `noop` | `../utils/is` |


---

## Functions

### `toRef(r: () => T): Readonly<Ref<T>>`

<details><summary>Code</summary>

```ts
export function toRef<T>(r: () => T): Readonly<Ref<T>>
```
</details>

- **JSDoc**:
```ts
/**
 * Normalize value/ref/getter to `ref` or `computed`.
 */
```

- **Parameters**:
  - `r: () => T`
- **Return Type**: `Readonly<Ref<T>>`

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