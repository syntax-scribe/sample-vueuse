[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 114
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 1
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/shared/useDateFormat/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `defaultMeridiem(hours: number, minutes: number, isLowercase: boolean, hasPeriod: boolean): string`

<details><summary>Code</summary>

```ts
function defaultMeridiem(hours: number, minutes: number, isLowercase?: boolean, hasPeriod?: boolean) {
  let m = (hours < 12 ? 'AM' : 'PM')
  if (hasPeriod)
    m = m.split('').reduce((acc, curr) => acc += `${curr}.`, '')
  return isLowercase ? m.toLowerCase() : m
}
```
</details>

- **Parameters**:
  - `hours: number`
  - `minutes: number`
  - `isLowercase: boolean`
  - `hasPeriod: boolean`
- **Return Type**: `string`
- **Calls**:
  - `m.split('').reduce`
  - `m.toLowerCase`
### `formatOrdinal(num: number): string`

<details><summary>Code</summary>

```ts
function formatOrdinal(num: number) {
  const suffixes = ['th', 'st', 'nd', 'rd']
  const v = num % 100
  return num + (suffixes[(v - 20) % 10] || suffixes[v] || suffixes[0])
}
```
</details>

- **Parameters**:
  - `num: number`
- **Return Type**: `string`
### `formatDate(date: Date, formatStr: string, options: UseDateFormatOptions): string`

<details><summary>Code</summary>

```ts
export function formatDate(date: Date, formatStr: string, options: UseDateFormatOptions = {}) {
  const years = date.getFullYear()
  const month = date.getMonth()
  const days = date.getDate()
  const hours = date.getHours()
  const minutes = date.getMinutes()
  const seconds = date.getSeconds()
  const milliseconds = date.getMilliseconds()
  const day = date.getDay()
  const meridiem = options.customMeridiem ?? defaultMeridiem
  const stripTimeZone = (dateString: string) => {
    return dateString.split(' ')[1] ?? ''
  }
  const matches: Record<string, () => string | number> = {
    Yo: () => formatOrdinal(years),
    YY: () => String(years).slice(-2),
    YYYY: () => years,
    M: () => month + 1,
    Mo: () => formatOrdinal(month + 1),
    MM: () => `${month + 1}`.padStart(2, '0'),
    MMM: () => date.toLocaleDateString(toValue(options.locales), { month: 'short' }),
    MMMM: () => date.toLocaleDateString(toValue(options.locales), { month: 'long' }),
    D: () => String(days),
    Do: () => formatOrdinal(days),
    DD: () => `${days}`.padStart(2, '0'),
    H: () => String(hours),
    Ho: () => formatOrdinal(hours),
    HH: () => `${hours}`.padStart(2, '0'),
    h: () => `${hours % 12 || 12}`.padStart(1, '0'),
    ho: () => formatOrdinal(hours % 12 || 12),
    hh: () => `${hours % 12 || 12}`.padStart(2, '0'),
    m: () => String(minutes),
    mo: () => formatOrdinal(minutes),
    mm: () => `${minutes}`.padStart(2, '0'),
    s: () => String(seconds),
    so: () => formatOrdinal(seconds),
    ss: () => `${seconds}`.padStart(2, '0'),
    SSS: () => `${milliseconds}`.padStart(3, '0'),
    d: () => day,
    dd: () => date.toLocaleDateString(toValue(options.locales), { weekday: 'narrow' }),
    ddd: () => date.toLocaleDateString(toValue(options.locales), { weekday: 'short' }),
    dddd: () => date.toLocaleDateString(toValue(options.locales), { weekday: 'long' }),
    A: () => meridiem(hours, minutes),
    AA: () => meridiem(hours, minutes, false, true),
    a: () => meridiem(hours, minutes, true),
    aa: () => meridiem(hours, minutes, true, true),
    z: () => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' })),
    zz: () => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' })),
    zzz: () => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' })),
    zzzz: () => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'longOffset' })),
  }
  return formatStr.replace(REGEX_FORMAT, (match, $1) => $1 ?? matches[match]?.() ?? match)
}
```
</details>

- **Parameters**:
  - `date: Date`
  - `formatStr: string`
  - `options: UseDateFormatOptions`
- **Return Type**: `string`
- **Calls**:
  - `date.getFullYear`
  - `date.getMonth`
  - `date.getDate`
  - `date.getHours`
  - `date.getMinutes`
  - `date.getSeconds`
  - `date.getMilliseconds`
  - `date.getDay`
  - `dateString.split`
  - `formatOrdinal`
  - `String(years).slice`
  - ``${month + 1}`.padStart`
  - `date.toLocaleDateString`
  - `toValue (from vue)`
  - `String`
  - ``${days}`.padStart`
  - ``${hours}`.padStart`
  - ``${hours % 12 || 12}`.padStart`
  - ``${minutes}`.padStart`
  - ``${seconds}`.padStart`
  - ``${milliseconds}`.padStart`
  - `meridiem`
  - `stripTimeZone`
  - `formatStr.replace`
  - `complex_call_4024`
### `stripTimeZone(dateString: string): string`

<details><summary>Code</summary>

```ts
(dateString: string) => {
    return dateString.split(' ')[1] ?? ''
  }
```
</details>

- **Parameters**:
  - `dateString: string`
- **Return Type**: `string`
- **Calls**:
  - `dateString.split`
### `Yo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(years)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `YY(): string`

<details><summary>Code</summary>

```ts
() => String(years).slice(-2)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String(years).slice`
### `YYYY(): number`

<details><summary>Code</summary>

```ts
() => years
```
</details>

- **Return Type**: `number`
### `M(): number`

<details><summary>Code</summary>

```ts
() => month + 1
```
</details>

- **Return Type**: `number`
### `Mo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(month + 1)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `MM(): string`

<details><summary>Code</summary>

```ts
() => `${month + 1}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${month + 1}`.padStart`
### `MMM(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { month: 'short' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `MMMM(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { month: 'long' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `D(): string`

<details><summary>Code</summary>

```ts
() => String(days)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `Do(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(days)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `DD(): string`

<details><summary>Code</summary>

```ts
() => `${days}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${days}`.padStart`
### `H(): string`

<details><summary>Code</summary>

```ts
() => String(hours)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `Ho(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(hours)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `HH(): string`

<details><summary>Code</summary>

```ts
() => `${hours}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours}`.padStart`
### `h(): string`

<details><summary>Code</summary>

```ts
() => `${hours % 12 || 12}`.padStart(1, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours % 12 || 12}`.padStart`
### `ho(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(hours % 12 || 12)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `hh(): string`

<details><summary>Code</summary>

```ts
() => `${hours % 12 || 12}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours % 12 || 12}`.padStart`
### `m(): string`

<details><summary>Code</summary>

```ts
() => String(minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `mo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `mm(): string`

<details><summary>Code</summary>

```ts
() => `${minutes}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${minutes}`.padStart`
### `s(): string`

<details><summary>Code</summary>

```ts
() => String(seconds)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `so(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(seconds)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `ss(): string`

<details><summary>Code</summary>

```ts
() => `${seconds}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${seconds}`.padStart`
### `SSS(): string`

<details><summary>Code</summary>

```ts
() => `${milliseconds}`.padStart(3, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${milliseconds}`.padStart`
### `d(): number`

<details><summary>Code</summary>

```ts
() => day
```
</details>

- **Return Type**: `number`
### `dd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'narrow' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `ddd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'short' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `dddd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'long' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `A(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `AA(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, false, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `a(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `aa(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, true, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `z(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zzz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zzzz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'longOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `Yo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(years)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `YY(): string`

<details><summary>Code</summary>

```ts
() => String(years).slice(-2)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String(years).slice`
### `YYYY(): number`

<details><summary>Code</summary>

```ts
() => years
```
</details>

- **Return Type**: `number`
### `M(): number`

<details><summary>Code</summary>

```ts
() => month + 1
```
</details>

- **Return Type**: `number`
### `Mo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(month + 1)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `MM(): string`

<details><summary>Code</summary>

```ts
() => `${month + 1}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${month + 1}`.padStart`
### `MMM(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { month: 'short' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `MMMM(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { month: 'long' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `D(): string`

<details><summary>Code</summary>

```ts
() => String(days)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `Do(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(days)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `DD(): string`

<details><summary>Code</summary>

```ts
() => `${days}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${days}`.padStart`
### `H(): string`

<details><summary>Code</summary>

```ts
() => String(hours)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `Ho(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(hours)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `HH(): string`

<details><summary>Code</summary>

```ts
() => `${hours}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours}`.padStart`
### `h(): string`

<details><summary>Code</summary>

```ts
() => `${hours % 12 || 12}`.padStart(1, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours % 12 || 12}`.padStart`
### `ho(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(hours % 12 || 12)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `hh(): string`

<details><summary>Code</summary>

```ts
() => `${hours % 12 || 12}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours % 12 || 12}`.padStart`
### `m(): string`

<details><summary>Code</summary>

```ts
() => String(minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `mo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `mm(): string`

<details><summary>Code</summary>

```ts
() => `${minutes}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${minutes}`.padStart`
### `s(): string`

<details><summary>Code</summary>

```ts
() => String(seconds)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `so(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(seconds)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `ss(): string`

<details><summary>Code</summary>

```ts
() => `${seconds}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${seconds}`.padStart`
### `SSS(): string`

<details><summary>Code</summary>

```ts
() => `${milliseconds}`.padStart(3, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${milliseconds}`.padStart`
### `d(): number`

<details><summary>Code</summary>

```ts
() => day
```
</details>

- **Return Type**: `number`
### `dd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'narrow' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `ddd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'short' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `dddd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'long' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `A(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `AA(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, false, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `a(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `aa(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, true, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `z(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zzz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zzzz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'longOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `Yo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(years)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `YY(): string`

<details><summary>Code</summary>

```ts
() => String(years).slice(-2)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String(years).slice`
### `YYYY(): number`

<details><summary>Code</summary>

```ts
() => years
```
</details>

- **Return Type**: `number`
### `M(): number`

<details><summary>Code</summary>

```ts
() => month + 1
```
</details>

- **Return Type**: `number`
### `Mo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(month + 1)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `MM(): string`

<details><summary>Code</summary>

```ts
() => `${month + 1}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${month + 1}`.padStart`
### `MMM(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { month: 'short' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `MMMM(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { month: 'long' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `D(): string`

<details><summary>Code</summary>

```ts
() => String(days)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `Do(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(days)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `DD(): string`

<details><summary>Code</summary>

```ts
() => `${days}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${days}`.padStart`
### `H(): string`

<details><summary>Code</summary>

```ts
() => String(hours)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `Ho(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(hours)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `HH(): string`

<details><summary>Code</summary>

```ts
() => `${hours}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours}`.padStart`
### `h(): string`

<details><summary>Code</summary>

```ts
() => `${hours % 12 || 12}`.padStart(1, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours % 12 || 12}`.padStart`
### `ho(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(hours % 12 || 12)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `hh(): string`

<details><summary>Code</summary>

```ts
() => `${hours % 12 || 12}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${hours % 12 || 12}`.padStart`
### `m(): string`

<details><summary>Code</summary>

```ts
() => String(minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `mo(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `mm(): string`

<details><summary>Code</summary>

```ts
() => `${minutes}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${minutes}`.padStart`
### `s(): string`

<details><summary>Code</summary>

```ts
() => String(seconds)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `String`
### `so(): string`

<details><summary>Code</summary>

```ts
() => formatOrdinal(seconds)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `formatOrdinal`
### `ss(): string`

<details><summary>Code</summary>

```ts
() => `${seconds}`.padStart(2, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${seconds}`.padStart`
### `SSS(): string`

<details><summary>Code</summary>

```ts
() => `${milliseconds}`.padStart(3, '0')
```
</details>

- **Return Type**: `string`
- **Calls**:
  - ``${milliseconds}`.padStart`
### `d(): number`

<details><summary>Code</summary>

```ts
() => day
```
</details>

- **Return Type**: `number`
### `dd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'narrow' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `ddd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'short' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `dddd(): string`

<details><summary>Code</summary>

```ts
() => date.toLocaleDateString(toValue(options.locales), { weekday: 'long' })
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `date.toLocaleDateString`
### `A(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `AA(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, false, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `a(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `aa(): string`

<details><summary>Code</summary>

```ts
() => meridiem(hours, minutes, true, true)
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `meridiem`
### `z(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zzz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'shortOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `zzzz(): string`

<details><summary>Code</summary>

```ts
() => stripTimeZone(date.toLocaleDateString(toValue(options.locales), { timeZoneName: 'longOffset' }))
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `stripTimeZone`
### `normalizeDate(date: DateLike): Date`

<details><summary>Code</summary>

```ts
export function normalizeDate(date: DateLike) {
  if (date === null)
    return new Date(Number.NaN) // null is invalid
  if (date === undefined)
    return new Date()
  if (date instanceof Date)
    return new Date(date)
  if (typeof date === 'string' && !/Z$/i.test(date)) {
    const d = date.match(REGEX_PARSE) as any
    if (d) {
      const m = d[2] - 1 || 0
      const ms = (d[7] || '0').substring(0, 3)
      return new Date(d[1], m, d[3]
        || 1, d[4] || 0, d[5] || 0, d[6] || 0, ms)
    }
  }

  return new Date(date)
}
```
</details>

- **Parameters**:
  - `date: DateLike`
- **Return Type**: `Date`
- **Calls**:
  - `/Z$/i.test`
  - `date.match`
  - `(d[7] || '0').substring`
### `useDateFormat(date: MaybeRefOrGetter<DateLike>, formatStr: MaybeRefOrGetter<string>, options: UseDateFormatOptions): UseDateFormatReturn`

<details><summary>Code</summary>

```ts
export function useDateFormat(date: MaybeRefOrGetter<DateLike>, formatStr: MaybeRefOrGetter<string> = 'HH:mm:ss', options: UseDateFormatOptions = {}): UseDateFormatReturn {
  return computed(() => formatDate(normalizeDate(toValue(date)), toValue(formatStr), options))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Get the formatted date according to the string of tokens passed in.
 *
 * @see https://vueuse.org/useDateFormat
 * @param date - The date to format, can either be a `Date` object, a timestamp, or a string
 * @param formatStr - The combination of tokens to format the date
 * @param options - UseDateFormatOptions
 */
```

- **Parameters**:
  - `date: MaybeRefOrGetter<DateLike>`
  - `formatStr: MaybeRefOrGetter<string>`
  - `options: UseDateFormatOptions`
- **Return Type**: `UseDateFormatReturn`
- **Calls**:
  - `computed (from vue)`
  - `formatDate`
  - `normalizeDate`
  - `toValue (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseDateFormatOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseDateFormatOptions {
  /**
   * The locale(s) to used for dd/ddd/dddd/MMM/MMMM format
   *
   * [MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl#locales_argument).
   */
  locales?: MaybeRefOrGetter<Intl.LocalesArgument>

  /**
   * A custom function to re-modify the way to display meridiem
   *
   */
  customMeridiem?: (hours: number, minutes: number, isLowercase?: boolean, hasPeriod?: boolean) => string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `locales` | `MaybeRefOrGetter<Intl.LocalesArgument>` | ✓ |  |
| `customMeridiem` | `(hours: number, minutes: number, isLowercase?: boolean, hasPeriod?: boolean) => string` | ✓ |  |


---

## Type Aliases

### `DateLike`

```ts
type DateLike = Date | number | string | undefined;
```

### `UseDateFormatReturn`

```ts
type UseDateFormatReturn = ComputedRef<string>;
```


---