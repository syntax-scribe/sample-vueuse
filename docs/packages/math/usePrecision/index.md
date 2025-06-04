[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/math/usePrecision/index.ts`**

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
| `decimalPlaces` | `number` | const | `valueStr.split('.')[1].length` | ✗ |
| `multiplier` | `number` | const | `10 ** decimalPlaces` | ✗ |
| `power` | `number` | const | `10 ** _digits` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `accurateMultiply(value: number, power: number): number`

<details><summary>Code</summary>

```ts
function accurateMultiply(value: number, power: number): number {
  const valueStr = value.toString()

  if (value > 0 && valueStr.includes('.')) {
    const decimalPlaces = valueStr.split('.')[1].length
    const multiplier = 10 ** decimalPlaces

    return (value * multiplier * power) / multiplier
  }
  else {
    return value * power
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Accuracy of handling numerical values.
 *
 * @param value - The value
 * @param power - The power
 * @returns The result of multiplying the value with the power
 */
```

- **Parameters**:
  - `value: number`
  - `power: number`
- **Return Type**: `number`
- **Calls**:
  - `value.toString`
  - `valueStr.includes`
  - `valueStr.split`
### `usePrecision(value: MaybeRefOrGetter<number>, digits: MaybeRefOrGetter<number>, options: MaybeRefOrGetter<UsePrecisionOptions>): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function usePrecision(
  value: MaybeRefOrGetter<number>,
  digits: MaybeRefOrGetter<number>,
  options?: MaybeRefOrGetter<UsePrecisionOptions>,
): ComputedRef<number> {
  return computed<number>(() => {
    const _value = toValue(value)
    const _digits = toValue(digits)
    const power = 10 ** _digits
    return Math[toValue(options)?.math || 'round'](accurateMultiply(_value, power)) / power
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively set the precision of a number.
 *
 * @see https://vueuse.org/usePrecision
 */
```

- **Parameters**:
  - `value: MaybeRefOrGetter<number>`
  - `digits: MaybeRefOrGetter<number>`
  - `options: MaybeRefOrGetter<UsePrecisionOptions>`
- **Return Type**: `ComputedRef<number>`
- **Calls**:
  - `computed (from vue)`
  - `toValue (from vue)`
  - `complex_call_1185`
  - `accurateMultiply`

---

## Interfaces

### `UsePrecisionOptions`

<details><summary>Interface Code</summary>

```ts
export interface UsePrecisionOptions {
  /**
   * Method to use for rounding
   *
   * @default 'round'
   */
  math?: 'floor' | 'ceil' | 'round'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `math` | `'floor' | 'ceil' | 'round'` | ✓ |  |


---