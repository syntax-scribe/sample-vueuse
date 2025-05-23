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
- **Imports**: 4
- **Interfaces**: 2
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/useMemory/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `UseIntervalFnOptions` | `@vueuse/shared` |
| `useIntervalFn` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useMemory(options: UseMemoryOptions): { isSupported: any; memory: any; }`

<details><summary>Code</summary>

```ts
export function useMemory(options: UseMemoryOptions = {}) {
  const memory = deepRef<MemoryInfo>()
  const isSupported = useSupported(() => typeof performance !== 'undefined' && 'memory' in performance)

  if (isSupported.value) {
    const { interval = 1000 } = options
    useIntervalFn(() => {
      memory.value = (performance as PerformanceMemory).memory
    }, interval, { immediate: options.immediate, immediateCallback: options.immediateCallback })
  }

  return { isSupported, memory }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Memory Info.
 *
 * @see https://vueuse.org/useMemory
 * @param options
 */
```

- **Parameters**:
  - `options: UseMemoryOptions`
- **Return Type**: `{ isSupported: any; memory: any; }`
- **Calls**:
  - `deepRef (from vue)`
  - `useSupported (from ../useSupported)`
  - `useIntervalFn (from @vueuse/shared)`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `MemoryInfo`

<details><summary>Interface Code</summary>

```ts
export interface MemoryInfo {
  /**
   * The maximum size of the heap, in bytes, that is available to the context.
   */
  readonly jsHeapSizeLimit: number
  /**
   *  The total allocated heap size, in bytes.
   */
  readonly totalJSHeapSize: number
  /**
   * The currently active segment of JS heap, in bytes.
   */
  readonly usedJSHeapSize: number

  [Symbol.toStringTag]: 'MemoryInfo'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `jsHeapSizeLimit` | `number` | ✗ |  |
| `totalJSHeapSize` | `number` | ✗ |  |
| `usedJSHeapSize` | `number` | ✗ |  |
| `[Symbol.toStringTag]` | `'MemoryInfo'` | ✗ |  |

### `UseMemoryOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseMemoryOptions extends UseIntervalFnOptions {
  interval?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `interval` | `number` | ✓ |  |


---

## Type Aliases

### `PerformanceMemory`

```ts
type PerformanceMemory = Performance & {
  memory: MemoryInfo
};
```

### `UseMemoryReturn`

```ts
type UseMemoryReturn = ReturnType<typeof useMemory>;
```


---