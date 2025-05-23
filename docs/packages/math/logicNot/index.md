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
📂 **`packages/math/logicNot/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `logicNot(v: MaybeRefOrGetter<any>): ComputedRef<boolean>`

<details><summary>Code</summary>

```ts
export function logicNot(v: MaybeRefOrGetter<any>): ComputedRef<boolean> {
  return computed(() => !toValue(v))
}
```
</details>

- **JSDoc**:
```ts
/**
 * `NOT` conditions for refs.
 *
 * @see https://vueuse.org/logicNot
 */
```

- **Parameters**:
  - `v: MaybeRefOrGetter<any>`
- **Return Type**: `ComputedRef<boolean>`
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