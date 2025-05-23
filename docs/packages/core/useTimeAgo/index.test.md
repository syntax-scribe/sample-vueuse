[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `TimeUnit`

```ts
type TimeUnit = 'second' | 'minute' | 'hour' | 'day' | 'week' | 'month' | 'year';
```


---