[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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