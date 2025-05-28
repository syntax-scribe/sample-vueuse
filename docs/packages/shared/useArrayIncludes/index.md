[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 5 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/useArrayIncludes/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |
| `containsProp` | `../utils` |
| `isObject` | `../utils` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `list` | `MaybeRefOrGetter<MaybeRefOrGetter<T>[]>` | const | `args[0]` | ✗ |
| `value` | `MaybeRefOrGetter<V>` | const | `args[1]` | ✗ |
| `comparator` | `UseArrayIncludesComparatorFn<T, V>` | let/var | `args[2]` | ✗ |
| `formIndex` | `number` | let/var | `0` | ✗ |
| `key` | `keyof T` | const | `comparator as keyof T` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `isArrayIncludesOptions(obj: any): obj is UseArrayIncludesOptions<T, V>`

<details><summary>Code</summary>

```ts
function isArrayIncludesOptions<T, V>(obj: any): obj is UseArrayIncludesOptions<T, V> {
  return isObject(obj) && containsProp(obj, 'formIndex', 'comparator')
}
```
</details>

- **Parameters**:
  - `obj: any`
- **Return Type**: `obj is UseArrayIncludesOptions<T, V>`
- **Calls**:
  - `isObject (from ../utils)`
  - `containsProp (from ../utils)`
### `useArrayIncludes(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, value: MaybeRefOrGetter<V>, comparator: UseArrayIncludesComparatorFn<T, V>): UseArrayIncludesReturn`

<details><summary>Code</summary>

```ts
export function useArrayIncludes<T, V = any>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  value: MaybeRefOrGetter<V>,
  comparator?: UseArrayIncludesComparatorFn<T, V>,
): UseArrayIncludesReturn
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.includes`
 *
 * @see https://vueuse.org/useArrayIncludes
 *
 * @returns true if the `value` is found in the array. Otherwise, false.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `value: MaybeRefOrGetter<V>`
  - `comparator: UseArrayIncludesComparatorFn<T, V>`
- **Return Type**: `UseArrayIncludesReturn`

---

## Interfaces

### `UseArrayIncludesOptions<T, V>`

<details><summary>Interface Code</summary>

```ts
export interface UseArrayIncludesOptions<T, V> {
  fromIndex?: number
  comparator?: UseArrayIncludesComparatorFn<T, V> | keyof T
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `fromIndex` | `number` | ✓ |  |
| `comparator` | `UseArrayIncludesComparatorFn<T, V> | keyof T` | ✓ |  |


---

## Type Aliases

### `UseArrayIncludesComparatorFn<T, V>`

```ts
type UseArrayIncludesComparatorFn<T, V> = ((element: T, value: V, index: number, array: MaybeRefOrGetter<T>[]) => boolean);
```

### `UseArrayIncludesReturn`

```ts
type UseArrayIncludesReturn = ComputedRef<boolean>;
```


---