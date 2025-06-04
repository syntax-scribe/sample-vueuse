[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useNow/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `Ref` | `vue` |
| `useIntervalFn` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `useRafFn` | `../useRafFn` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `controls` | `Pausable` | const | `interval === 'requestAnimationFrame'
    ? useRafFn(update, { immediate })
    : useIntervalFn(update, interval, { immediate })` | ✗ |


---

## Functions

### `useNow(options: UseNowOptions<false>): Ref<Date>`

<details><summary>Code</summary>

```ts
export function useNow(options?: UseNowOptions<false>): Ref<Date>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive current Date instance.
 *
 * @see https://vueuse.org/useNow
 * @param options
 */
```

- **Parameters**:
  - `options: UseNowOptions<false>`
- **Return Type**: `Ref<Date>`
### `update(): Date`

<details><summary>Code</summary>

```ts
() => now.value = new Date()
```
</details>

- **Return Type**: `Date`

---

## Interfaces

### `UseNowOptions<Controls extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface UseNowOptions<Controls extends boolean> {
  /**
   * Expose more controls
   *
   * @default false
   */
  controls?: Controls

  /**
   * Start the clock immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Update interval in milliseconds, or use requestAnimationFrame
   *
   * @default requestAnimationFrame
   */
  interval?: 'requestAnimationFrame' | number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `controls` | `Controls` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `interval` | `'requestAnimationFrame' | number` | ✓ |  |


---

## Type Aliases

### `UseNowReturn`

```ts
type UseNowReturn = ReturnType<typeof useNow>;
```


---