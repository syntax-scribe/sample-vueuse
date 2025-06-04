[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `r` | `any` | const | `args[0]` | ✗ |
| `resolveRef` | `{ <T>(r: () => T): Ref<T>; <T>(r: ComputedRef<T>): ComputedRef<T>; <T>(r: MaybeRefOrGetter<T>): Ref<T>; <T>(r: T): Ref<T>; <T extends object, K extends keyof T>(object: T, key: K): ToRef<T[K]>; <T extends object, K extends keyof T>(object: T, key: K, defaultValue: T[K]): ToRef<...>; }` | const | `toRef` | ✓ |


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