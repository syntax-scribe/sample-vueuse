[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


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