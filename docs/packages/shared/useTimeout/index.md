[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useTimeout/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `UseTimeoutFnOptions` | `../useTimeoutFn` |
| `Fn` | `../utils` |
| `Stoppable` | `../utils` |
| `computed` | `vue` |
| `useTimeoutFn` | `../useTimeoutFn` |
| `noop` | `../utils` |


---

## Functions

### `useTimeout(interval: MaybeRefOrGetter<number>, options: UseTimeoutOptions<false>): ComputedRef<boolean>`

<details><summary>Code</summary>

```ts
export function useTimeout(interval?: MaybeRefOrGetter<number>, options?: UseTimeoutOptions<false>): ComputedRef<boolean>
```
</details>

- **JSDoc**:
```ts
/**
 * Update value after a given time with controls.
 *
 * @see   {@link https://vueuse.org/useTimeout}
 * @param interval
 * @param options
 */
```

- **Parameters**:
  - `interval: MaybeRefOrGetter<number>`
  - `options: UseTimeoutOptions<false>`
- **Return Type**: `ComputedRef<boolean>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseTimeoutOptions<Controls extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface UseTimeoutOptions<Controls extends boolean> extends UseTimeoutFnOptions {
  /**
   * Expose more controls
   *
   * @default false
   */
  controls?: Controls
  /**
   * Callback on timeout
   */
  callback?: Fn
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `controls` | `Controls` | ✓ |  |
| `callback` | `Fn` | ✓ |  |


---

## Type Aliases

### `UseTimoutReturn`

```ts
type UseTimoutReturn = ComputedRef<boolean> | { readonly ready: ComputedRef<boolean> } & Stoppable;
```


---