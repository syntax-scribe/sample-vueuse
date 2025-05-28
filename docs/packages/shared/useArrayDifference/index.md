[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/useArrayDifference/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `list` | `MaybeRefOrGetter<T[]>` | const | `args[0]` | ✗ |
| `values` | `MaybeRefOrGetter<T[]>` | const | `args[1]` | ✗ |
| `compareFn` | `any` | let/var | `args[2] ?? defaultComparator` | ✗ |
| `key` | `keyof T` | const | `compareFn as keyof T` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `defaultComparator(value: T, othVal: T): boolean`

<details><summary>Code</summary>

```ts
function defaultComparator<T>(value: T, othVal: T) {
  return value === othVal
}
```
</details>

- **Parameters**:
  - `value: T`
  - `othVal: T`
- **Return Type**: `boolean`
### `useArrayDifference(list: MaybeRefOrGetter<T[]>, values: MaybeRefOrGetter<T[]>, key: keyof T, options: UseArrayDifferenceOptions): UseArrayDifferenceReturn<T>`

<details><summary>Code</summary>

```ts
export function useArrayDifference<T>(
  list: MaybeRefOrGetter<T[]>,
  values: MaybeRefOrGetter<T[]>,
  key?: keyof T,
  options?: UseArrayDifferenceOptions
): UseArrayDifferenceReturn<T>
```
</details>

- **Parameters**:
  - `list: MaybeRefOrGetter<T[]>`
  - `values: MaybeRefOrGetter<T[]>`
  - `key: keyof T`
  - `options: UseArrayDifferenceOptions`
- **Return Type**: `UseArrayDifferenceReturn<T>`

---

## Interfaces

### `UseArrayDifferenceOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseArrayDifferenceOptions {
  /**
   * Returns asymmetric difference
   *
   * @see https://en.wikipedia.org/wiki/Symmetric_difference
   * @default false
   */
  symmetric?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `symmetric` | `boolean` | ✓ |  |


---

## Type Aliases

### `UseArrayDifferenceReturn<T = any = any>`

```ts
type UseArrayDifferenceReturn<T = any = any> = ComputedRef<T[]>;
```


---