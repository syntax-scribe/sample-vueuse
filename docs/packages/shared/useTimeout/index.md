[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 8 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


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