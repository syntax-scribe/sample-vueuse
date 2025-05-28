[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/useToNumber/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useToNumber(value: MaybeRefOrGetter<number | string>, options: UseToNumberOptions): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function useToNumber(
  value: MaybeRefOrGetter<number | string>,
  options: UseToNumberOptions = {},
): ComputedRef<number> {
  const {
    method = 'parseFloat',
    radix,
    nanToZero,
  } = options

  return computed(() => {
    let resolved = toValue(value)
    if (typeof method === 'function')
      resolved = method(resolved)
    else if (typeof resolved === 'string')
      resolved = Number[method](resolved, radix)

    if (nanToZero && Number.isNaN(resolved))
      resolved = 0
    return resolved
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively convert a string ref to number.
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<number | string>`
  - `options: UseToNumberOptions`
- **Return Type**: `ComputedRef<number>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`
  - `method`
  - `complex_call_1048`
  - `Number.isNaN`

---

## Interfaces

### `UseToNumberOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseToNumberOptions {
  /**
   * Method to use to convert the value to a number.
   *
   * Or a custom function for the conversion.
   *
   * @default 'parseFloat'
   */
  method?: 'parseFloat' | 'parseInt' | ((value: string | number) => number)

  /**
   * The base in mathematical numeral systems passed to `parseInt`.
   * Only works with `method: 'parseInt'`
   */
  radix?: number

  /**
   * Replace NaN with zero
   *
   * @default false
   */
  nanToZero?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `method` | `'parseFloat' | 'parseInt' | ((value: string | number) => number)` | ✓ |  |
| `radix` | `number` | ✓ |  |
| `nanToZero` | `boolean` | ✓ |  |


---