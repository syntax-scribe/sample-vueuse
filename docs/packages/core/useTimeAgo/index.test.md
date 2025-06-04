[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 5 |
| 🟢 Vue Composition API | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useTimeAgo/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `timestamp` | `@vueuse/shared` |
| `afterEach` | `vitest` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `useTimeAgo` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `UNITS` | `{ max: number; value: number; name: string; }[]` | const | `[
  { max: 60000, value: 1000, name: 'second' },
  { max: 2760000, value: 60000, name: 'minute' },
  { max: 72000000, value: 3600000, name: 'hour' },
  { max: 518400000, value: 86400000, name: 'day' },
  { max: 2419200000, value: 604800000, name: 'week' },
  { max: 28512000000, value: 2592000000, name: 'month' },
  { max: Number.POSITIVE_INFINITY, value: 31536000000, name: 'year' },
]` | ✗ |
| `baseTime` | `number` | let/var | `*not shown*` | ✗ |
| `changeTime` | `ComputedRef<number>` | let/var | `*not shown*` | ✗ |
| `text` | `"past" | "future"` | const | `isFuture ? 'future' : 'past'` | ✗ |
| `nextTime` | `number` | const | `getNeededTimeChange('minute', 1, -1) * (isFuture ? 1 : -1)` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `fullDateFormatter(value: any): string`

<details><summary>Code</summary>

```ts
function fullDateFormatter(value: any) {
  return new Date(value).toISOString().slice(0, 10)
}
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `string`
- **Calls**:
  - `new Date(value).toISOString().slice`
### `getNeededTimeChange(type: TimeUnit, count: number, adjustSecond: number): number`

<details><summary>Code</summary>

```ts
function getNeededTimeChange(type: TimeUnit, count: number, adjustSecond?: number) {
  const unit = UNITS.find(i => i.name === type)
  return (unit?.value || 0) * count + (adjustSecond || 0) * 1000
}
```
</details>

- **Parameters**:
  - `type: TimeUnit`
  - `count: number`
  - `adjustSecond: number`
- **Return Type**: `number`
- **Calls**:
  - `UNITS.find`
### `reset(): void`

<details><summary>Code</summary>

```ts
function reset() {
    vi.useFakeTimers()
    baseTime = timestamp()
    vi.setSystemTime(baseTime)
    changeValue.value = 0
    changeTime = computed(() => baseTime + changeValue.value)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `vi.useFakeTimers`
  - `timestamp (from @vueuse/shared)`
  - `vi.setSystemTime`
  - `computed (from vue)`
### `testSecond(isFuture: boolean): void`

<details><summary>Code</summary>

```ts
function testSecond(isFuture: boolean) {
      const text = isFuture ? 'future' : 'past'
      const nextTime = getNeededTimeChange('minute', 1, -1) * (isFuture ? 1 : -1)
      it(`${text}: less than 1 minute`, () => {
        changeValue.value = nextTime
        expect(useTimeAgo(changeTime).value).toBe('just now')
      })

      it(`${text}: less than 1 second`, () => {
        changeValue.value = getNeededTimeChange('minute', 1, -59.6) * (isFuture ? 1 : -1)
        expect(useTimeAgo(changeTime, { showSecond: true }).value).toBe(
          isFuture ? 'in 0 second' : '0 second ago',
        )
      })

      it(`${text}: less than 1 minute/ with showSecond`, () => {
        changeValue.value = nextTime
        expect(useTimeAgo(changeTime, { showSecond: true }).value).toBe(
          isFuture ? 'in 59 seconds' : '59 seconds ago',
        )
      })

      it(`${text}: less than 1 minute but more than 10 seconds with showSecond`, () => {
        changeValue.value = nextTime
        expect(useTimeAgo(changeTime, { showSecond: true, max: 10000 }).value).toBe(fullDateFormatter(changeTime.value))
      })

      it(`${text}: more than 1 minute`, () => {
        changeValue.value = getNeededTimeChange('minute', 1, 1) * (isFuture ? 1 : -1)
        expect(useTimeAgo(changeTime, { showSecond: true, max: 'second' }).value).toBe(fullDateFormatter(changeTime.value))
      })
    }
```
</details>

- **Parameters**:
  - `isFuture: boolean`
- **Return Type**: `void`
- **Calls**:
  - `getNeededTimeChange`
  - `it (from vitest)`
  - `expect(useTimeAgo(changeTime).value).toBe`
  - `expect(useTimeAgo(changeTime, { showSecond: true }).value).toBe`
  - `expect(useTimeAgo(changeTime, { showSecond: true, max: 10000 }).value).toBe`
  - `fullDateFormatter`
  - `expect(useTimeAgo(changeTime, { showSecond: true, max: 'second' }).value).toBe`

---

## Type Aliases

### `TimeUnit`

```ts
type TimeUnit = 'second' | 'minute' | 'hour' | 'day' | 'week' | 'month' | 'year';
```


---