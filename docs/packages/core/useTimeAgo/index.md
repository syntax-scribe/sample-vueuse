[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 60 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 7 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 4 |
| 📑 Type Aliases | 4 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useTimeAgo/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |
| `useNow` | `../useNow` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `DEFAULT_UNITS` | `UseTimeAgoUnit<UseTimeAgoUnitNamesDefault>[]` | const | `[
  { max: 60000, value: 1000, name: 'second' },
  { max: 2760000, value: 60000, name: 'minute' },
  { max: 72000000, value: 3600000, name: 'hour' },
  { max: 518400000, value: 86400000, name: 'day' },
  { max: 2419200000, value: 604800000, name: 'week' },
  { max: 28512000000, value: 2592000000, name: 'month' },
  { max: Number.POSITIVE_INFINITY, value: 31536000000, name: 'year' },
]` | ✗ |
| `DEFAULT_MESSAGES` | `UseTimeAgoMessages<UseTimeAgoUnitNamesDefault>` | const | `{
  justNow: 'just now',
  past: n => n.match(/\d/) ? `${n} ago` : n,
  future: n => n.match(/\d/) ? `in ${n}` : n,
  month: (n, past) => n === 1
    ? past
      ? 'last month'
      : 'next month'
    : `${n} month${n > 1 ? 's' : ''}`,
  year: (n, past) => n === 1
    ? past
      ? 'last year'
      : 'next year'
    : `${n} year${n > 1 ? 's' : ''}`,
  day: (n, past) => n === 1
    ? past
      ? 'yesterday'
      : 'tomorrow'
    : `${n} day${n > 1 ? 's' : ''}`,
  week: (n, past) => n === 1
    ? past
      ? 'last week'
      : 'next week'
    : `${n} week${n > 1 ? 's' : ''}`,
  hour: n => `${n} hour${n > 1 ? 's' : ''}`,
  minute: n => `${n} minute${n > 1 ? 's' : ''}`,
  second: n => `${n} second${n > 1 ? 's' : ''}`,
  invalid: '',
}` | ✗ |
| `roundFn` | `(n: number) => number` | const | `typeof rounding === 'number'
    ? (n: number) => +n.toFixed(rounding)
    : Math[rounding]` | ✗ |
| `diff` | `number` | const | `+now - +from` | ✗ |
| `past` | `boolean` | const | `diff > 0` | ✗ |
| `formatter` | `UseTimeAgoMessages<UnitNames>[UnitNames | keyof UseTimeAgoMessagesBuiltIn]` | const | `messages[name]` | ✗ |
| `unitMax` | `number` | const | `units.find(i => i.name === max)?.max` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `past(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `${n} ago` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `future(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `in ${n}` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `month(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last month'
      : 'next month'
    : `${n} month${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `year(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last year'
      : 'next year'
    : `${n} year${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `day(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'yesterday'
      : 'tomorrow'
    : `${n} day${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `week(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last week'
      : 'next week'
    : `${n} week${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `hour(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} hour${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `minute(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} minute${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `second(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} second${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `past(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `${n} ago` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `future(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `in ${n}` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `month(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last month'
      : 'next month'
    : `${n} month${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `year(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last year'
      : 'next year'
    : `${n} year${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `day(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'yesterday'
      : 'tomorrow'
    : `${n} day${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `week(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last week'
      : 'next week'
    : `${n} week${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `hour(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} hour${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `minute(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} minute${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `second(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} second${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `past(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `${n} ago` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `future(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `in ${n}` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `month(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last month'
      : 'next month'
    : `${n} month${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `year(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last year'
      : 'next year'
    : `${n} year${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `day(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'yesterday'
      : 'tomorrow'
    : `${n} day${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `week(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last week'
      : 'next week'
    : `${n} week${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `hour(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} hour${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `minute(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} minute${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `second(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} second${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `past(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `${n} ago` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `future(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `in ${n}` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `month(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last month'
      : 'next month'
    : `${n} month${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `year(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last year'
      : 'next year'
    : `${n} year${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `day(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'yesterday'
      : 'tomorrow'
    : `${n} day${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `week(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last week'
      : 'next week'
    : `${n} week${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `hour(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} hour${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `minute(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} minute${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `second(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} second${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `past(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `${n} ago` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `future(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `in ${n}` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `month(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last month'
      : 'next month'
    : `${n} month${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `year(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last year'
      : 'next year'
    : `${n} year${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `day(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'yesterday'
      : 'tomorrow'
    : `${n} day${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `week(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last week'
      : 'next week'
    : `${n} week${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `hour(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} hour${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `minute(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} minute${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `second(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} second${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `past(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `${n} ago` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `future(n: string): string`

<details><summary>Code</summary>

```ts
n => n.match(/\d/) ? `in ${n}` : n
```
</details>

- **Parameters**:
  - `n: string`
- **Return Type**: `string`
### `month(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last month'
      : 'next month'
    : `${n} month${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `year(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last year'
      : 'next year'
    : `${n} year${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `day(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'yesterday'
      : 'tomorrow'
    : `${n} day${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `week(n: number, past: boolean): string`

<details><summary>Code</summary>

```ts
(n, past) => n === 1
    ? past
      ? 'last week'
      : 'next week'
    : `${n} week${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
  - `past: boolean`
- **Return Type**: `string`
### `hour(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} hour${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `minute(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} minute${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `second(n: number): string`

<details><summary>Code</summary>

```ts
n => `${n} second${n > 1 ? 's' : ''}`
```
</details>

- **Parameters**:
  - `n: number`
- **Return Type**: `string`
### `DEFAULT_FORMATTER(date: Date): string`

<details><summary>Code</summary>

```ts
function DEFAULT_FORMATTER(date: Date) {
  return date.toISOString().slice(0, 10)
}
```
</details>

- **Parameters**:
  - `date: Date`
- **Return Type**: `string`
- **Calls**:
  - `date.toISOString().slice`
### `useTimeAgo(time: MaybeRefOrGetter<Date | number | string>, options: UseTimeAgoOptions<false, UnitNames>): UseTimeAgoReturn<false>`

<details><summary>Code</summary>

```ts
export function useTimeAgo<UnitNames extends string = UseTimeAgoUnitNamesDefault>(time: MaybeRefOrGetter<Date | number | string>, options?: UseTimeAgoOptions<false, UnitNames>): UseTimeAgoReturn<false>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive time ago formatter.
 *
 * @see https://vueuse.org/useTimeAgo
 */
```

- **Parameters**:
  - `time: MaybeRefOrGetter<Date | number | string>`
  - `options: UseTimeAgoOptions<false, UnitNames>`
- **Return Type**: `UseTimeAgoReturn<false>`
### `formatTimeAgo(from: Date, options: FormatTimeAgoOptions<UnitNames>, now: Date | number): string`

<details><summary>Code</summary>

```ts
export function formatTimeAgo<UnitNames extends string = UseTimeAgoUnitNamesDefault>(from: Date, options: FormatTimeAgoOptions<UnitNames> = {}, now: Date | number = Date.now()): string {
  const {
    max,
    messages = DEFAULT_MESSAGES as UseTimeAgoMessages<UnitNames>,
    fullDateFormatter = DEFAULT_FORMATTER,
    units = DEFAULT_UNITS as UseTimeAgoUnit<UnitNames>[],
    showSecond = false,
    rounding = 'round',
  } = options

  const roundFn = typeof rounding === 'number'
    ? (n: number) => +n.toFixed(rounding)
    : Math[rounding]

  const diff = +now - +from
  const absDiff = Math.abs(diff)

  function getValue(diff: number, unit: UseTimeAgoUnit<UnitNames>) {
    return roundFn(Math.abs(diff) / unit.value)
  }

  function format(diff: number, unit: UseTimeAgoUnit<UnitNames>) {
    const val = getValue(diff, unit)
    const past = diff > 0

    const str = applyFormat(unit.name as UnitNames, val, past)
    return applyFormat(past ? 'past' : 'future', str, past)
  }

  function applyFormat(name: UnitNames | keyof UseTimeAgoMessagesBuiltIn, val: number | string, isPast: boolean) {
    const formatter = messages[name]
    if (typeof formatter === 'function')
      return formatter(val as never, isPast)
    return formatter.replace('{0}', val.toString())
  }

  // less than a minute
  if (absDiff < 60000 && !showSecond)
    return messages.justNow

  if (typeof max === 'number' && absDiff > max)
    return fullDateFormatter(new Date(from))

  if (typeof max === 'string') {
    const unitMax = units.find(i => i.name === max)?.max
    if (unitMax && absDiff > unitMax)
      return fullDateFormatter(new Date(from))
  }

  for (const [idx, unit] of units.entries()) {
    const val = getValue(diff, unit)
    if (val <= 0 && units[idx - 1])
      return format(diff, units[idx - 1])
    if (absDiff < unit.max)
      return format(diff, unit)
  }

  return messages.invalid
}
```
</details>

- **Parameters**:
  - `from: Date`
  - `options: FormatTimeAgoOptions<UnitNames>`
  - `now: Date | number`
- **Return Type**: `string`
- **Calls**:
  - `n.toFixed`
  - `Math.abs`
  - `roundFn`
  - `getValue`
  - `applyFormat`
  - `formatter`
  - `formatter.replace`
  - `val.toString`
  - `fullDateFormatter`
  - `units.find`
  - `units.entries`
  - `format`
- **Internal Comments**:
```
// less than a minute
```

### `getValue(diff: number, unit: UseTimeAgoUnit<UnitNames>): number`

<details><summary>Code</summary>

```ts
function getValue(diff: number, unit: UseTimeAgoUnit<UnitNames>) {
    return roundFn(Math.abs(diff) / unit.value)
  }
```
</details>

- **Parameters**:
  - `diff: number`
  - `unit: UseTimeAgoUnit<UnitNames>`
- **Return Type**: `number`
- **Calls**:
  - `roundFn`
  - `Math.abs`
### `format(diff: number, unit: UseTimeAgoUnit<UnitNames>): string`

<details><summary>Code</summary>

```ts
function format(diff: number, unit: UseTimeAgoUnit<UnitNames>) {
    const val = getValue(diff, unit)
    const past = diff > 0

    const str = applyFormat(unit.name as UnitNames, val, past)
    return applyFormat(past ? 'past' : 'future', str, past)
  }
```
</details>

- **Parameters**:
  - `diff: number`
  - `unit: UseTimeAgoUnit<UnitNames>`
- **Return Type**: `string`
- **Calls**:
  - `getValue`
  - `applyFormat`
### `applyFormat(name: UnitNames | keyof UseTimeAgoMessagesBuiltIn, val: number | string, isPast: boolean): string`

<details><summary>Code</summary>

```ts
function applyFormat(name: UnitNames | keyof UseTimeAgoMessagesBuiltIn, val: number | string, isPast: boolean) {
    const formatter = messages[name]
    if (typeof formatter === 'function')
      return formatter(val as never, isPast)
    return formatter.replace('{0}', val.toString())
  }
```
</details>

- **Parameters**:
  - `name: UnitNames | keyof UseTimeAgoMessagesBuiltIn`
  - `val: number | string`
  - `isPast: boolean`
- **Return Type**: `string`
- **Calls**:
  - `formatter`
  - `formatter.replace`
  - `val.toString`

---

## Interfaces

### `UseTimeAgoMessagesBuiltIn`

<details><summary>Interface Code</summary>

```ts
export interface UseTimeAgoMessagesBuiltIn {
  justNow: string
  past: string | UseTimeAgoFormatter<string>
  future: string | UseTimeAgoFormatter<string>
  invalid: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `justNow` | `string` | ✗ |  |
| `past` | `string | UseTimeAgoFormatter<string>` | ✗ |  |
| `future` | `string | UseTimeAgoFormatter<string>` | ✗ |  |
| `invalid` | `string` | ✗ |  |

### `FormatTimeAgoOptions<UnitNames extends string = UseTimeAgoUnitNamesDefault>`

<details><summary>Interface Code</summary>

```ts
export interface FormatTimeAgoOptions<UnitNames extends string = UseTimeAgoUnitNamesDefault> {
  /**
   * Maximum unit (of diff in milliseconds) to display the full date instead of relative
   *
   * @default undefined
   */
  max?: UnitNames | number

  /**
   * Formatter for full date
   */
  fullDateFormatter?: (date: Date) => string

  /**
   * Messages for formatting the string
   */
  messages?: UseTimeAgoMessages<UnitNames>

  /**
   * Minimum display time unit (default is minute)
   *
   * @default false
   */
  showSecond?: boolean

  /**
   * Rounding method to apply.
   *
   * @default 'round'
   */
  rounding?: 'round' | 'ceil' | 'floor' | number

  /**
   * Custom units
   */
  units?: UseTimeAgoUnit<UnitNames>[]
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `max` | `UnitNames | number` | ✓ |  |
| `fullDateFormatter` | `(date: Date) => string` | ✓ |  |
| `messages` | `UseTimeAgoMessages<UnitNames>` | ✓ |  |
| `showSecond` | `boolean` | ✓ |  |
| `rounding` | `'round' | 'ceil' | 'floor' | number` | ✓ |  |
| `units` | `UseTimeAgoUnit<UnitNames>[]` | ✓ |  |

### `UseTimeAgoOptions<Controls extends boolean, UnitNames extends string = UseTimeAgoUnitNamesDefault>`

<details><summary>Interface Code</summary>

```ts
export interface UseTimeAgoOptions<Controls extends boolean, UnitNames extends string = UseTimeAgoUnitNamesDefault> extends FormatTimeAgoOptions<UnitNames> {
  /**
   * Expose more controls
   *
   * @default false
   */
  controls?: Controls

  /**
   * Intervals to update, set 0 to disable auto update
   *
   * @default 30_000
   */
  updateInterval?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `controls` | `Controls` | ✓ |  |
| `updateInterval` | `number` | ✓ |  |

### `UseTimeAgoUnit<Unit extends string = UseTimeAgoUnitNamesDefault>`

<details><summary>Interface Code</summary>

```ts
export interface UseTimeAgoUnit<Unit extends string = UseTimeAgoUnitNamesDefault> {
  max: number
  value: number
  name: Unit
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `max` | `number` | ✗ |  |
| `value` | `number` | ✗ |  |
| `name` | `Unit` | ✗ |  |


---

## Type Aliases

### `UseTimeAgoFormatter<T = number = number>`

```ts
type UseTimeAgoFormatter<T = number = number> = (value: T, isPast: boolean) => string;
```

### `UseTimeAgoUnitNamesDefault`

```ts
type UseTimeAgoUnitNamesDefault = 'second' | 'minute' | 'hour' | 'day' | 'week' | 'month' | 'year';
```

### `UseTimeAgoMessages<UnitNames extends string = UseTimeAgoUnitNamesDefault extends string = UseTimeAgoUnitNamesDefault>`

```ts
type UseTimeAgoMessages<UnitNames extends string = UseTimeAgoUnitNamesDefault extends string = UseTimeAgoUnitNamesDefault> = UseTimeAgoMessagesBuiltIn
    & Record<UnitNames, string | UseTimeAgoFormatter<number>>;
```

### `UseTimeAgoReturn<Controls extends boolean = false extends boolean = false>`

```ts
type UseTimeAgoReturn<Controls extends boolean = false extends boolean = false> = Controls extends true ? { timeAgo: ComputedRef<string> } & Pausable : ComputedRef<string>;
```


---