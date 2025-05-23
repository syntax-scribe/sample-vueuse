[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/whenever/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchCallback` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `nextTick` | `vue` |
| `watch` | `vue` |


---

## Functions

### `whenever(source: WatchSource<T | false | null | undefined>, cb: WatchCallback<T>, options: WheneverOptions): any`

<details><summary>Code</summary>

```ts
export function whenever<T>(source: WatchSource<T | false | null | undefined>, cb: WatchCallback<T>, options?: WheneverOptions) {
  const stop = watch(
    source,
    (v, ov, onInvalidate) => {
      if (v) {
        if (options?.once)
          nextTick(() => stop())
        cb(v, ov, onInvalidate)
      }
    },
    {
      ...options,
      once: false,
    } as WatchOptions,
  )
  return stop
}
```
</details>

- **JSDoc**:
```ts
/**
 * Shorthand for watching value to be truthy
 *
 * @see https://vueuse.org/whenever
 */
```

- **Parameters**:
  - `source: WatchSource<T | false | null | undefined>`
  - `cb: WatchCallback<T>`
  - `options: WheneverOptions`
- **Return Type**: `any`
- **Calls**:
  - `watch (from vue)`
  - `nextTick (from vue)`
  - `stop`
  - `cb`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `WheneverOptions`

<details><summary>Interface Code</summary>

```ts
export interface WheneverOptions extends WatchOptions {
  /**
   * Only trigger once when the condition is met
   *
   * Override the `once` option in `WatchOptions`
   *
   * @default false
   */
  once?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `once` | `boolean` | ✓ |  |


---

## Type Aliases

> No type aliases found in this file.


---