[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useInterval/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `Pausable` | `../utils` |
| `shallowReadonly` | `vue` |
| `shallowRef` | `vue` |
| `useIntervalFn` | `../useIntervalFn` |


---

## Functions

### `useInterval(interval: MaybeRefOrGetter<number>, options: UseIntervalOptions<false>): Readonly<ShallowRef<number>>`

<details><summary>Code</summary>

```ts
export function useInterval(interval?: MaybeRefOrGetter<number>, options?: UseIntervalOptions<false>): Readonly<ShallowRef<number>>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive counter increases on every interval
 *
 * @see https://vueuse.org/useInterval
 * @param interval
 * @param options
 */
```

- **Parameters**:
  - `interval: MaybeRefOrGetter<number>`
  - `options: UseIntervalOptions<false>`
- **Return Type**: `Readonly<ShallowRef<number>>`
### `update(): any`

<details><summary>Code</summary>

```ts
() => counter.value += 1
```
</details>

- **Return Type**: `any`
### `reset(): void`

<details><summary>Code</summary>

```ts
() => {
    counter.value = 0
  }
```
</details>

- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseIntervalOptions<Controls extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface UseIntervalOptions<Controls extends boolean> {
  /**
   * Expose more controls
   *
   * @default false
   */
  controls?: Controls

  /**
   * Execute the update immediately on calling
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Callback on every interval
   */
  callback?: (count: number) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `controls` | `Controls` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `callback` | `(count: number) => void` | ✓ |  |

### `UseIntervalControls`

<details><summary>Interface Code</summary>

```ts
export interface UseIntervalControls {
  counter: ShallowRef<number>
  reset: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `counter` | `ShallowRef<number>` | ✗ |  |
| `reset` | `() => void` | ✗ |  |


---

## Type Aliases

### `UseIntervalReturn`

```ts
type UseIntervalReturn = Readonly<ShallowRef<number>> | Readonly<UseIntervalControls & Pausable>;
```


---