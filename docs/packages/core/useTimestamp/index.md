[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useTimestamp/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `ShallowRef` | `vue` |
| `timestamp` | `@vueuse/shared` |
| `useIntervalFn` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `useRafFn` | `../useRafFn` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `cb` | `() => void` | const | `callback
    ? () => {
        update()
        callback(ts.value)
      }
    : update` | ✗ |
| `controls` | `Pausable` | const | `interval === 'requestAnimationFrame'
    ? useRafFn(cb, { immediate })
    : useIntervalFn(cb, interval, { immediate })` | ✗ |


---

## Functions

### `useTimestamp(options: UseTimestampOptions<false>): ShallowRef<number>`

<details><summary>Code</summary>

```ts
export function useTimestamp(options?: UseTimestampOptions<false>): ShallowRef<number>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive current timestamp.
 *
 * @see https://vueuse.org/useTimestamp
 * @param options
 */
```

- **Parameters**:
  - `options: UseTimestampOptions<false>`
- **Return Type**: `ShallowRef<number>`
### `update(): any`

<details><summary>Code</summary>

```ts
() => ts.value = timestamp() + offset
```
</details>

- **Return Type**: `any`

---

## Interfaces

### `UseTimestampOptions<Controls extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface UseTimestampOptions<Controls extends boolean> {
  /**
   * Expose more controls
   *
   * @default false
   */
  controls?: Controls

  /**
   * Offset value adding to the value
   *
   * @default 0
   */
  offset?: number

  /**
   * Update the timestamp immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Update interval, or use requestAnimationFrame
   *
   * @default requestAnimationFrame
   */
  interval?: 'requestAnimationFrame' | number
  /**
   * Callback on each update
   */
  callback?: (timestamp: number) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `controls` | `Controls` | ✓ |  |
| `offset` | `number` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `interval` | `'requestAnimationFrame' | number` | ✓ |  |
| `callback` | `(timestamp: number) => void` | ✓ |  |


---

## Type Aliases

### `UseTimestampReturn`

```ts
type UseTimestampReturn = ReturnType<typeof useTimestamp>;
```


---