[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/usePerformanceObserver/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableWindow` | `../_configurable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `defaultWindow` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `observer` | `PerformanceObserver | undefined` | let/var | `*not shown*` | ✗ |


---

## Functions

### `usePerformanceObserver(options: UsePerformanceObserverOptions, callback: PerformanceObserverCallback): { isSupported: any; start: () => void; stop: () => void; }`

<details><summary>Code</summary>

```ts
export function usePerformanceObserver(options: UsePerformanceObserverOptions, callback: PerformanceObserverCallback) {
  const {
    window = defaultWindow,
    immediate = true,
    ...performanceOptions
  } = options

  const isSupported = useSupported(() => window && 'PerformanceObserver' in window)

  let observer: PerformanceObserver | undefined

  const stop = () => {
    observer?.disconnect()
  }

  const start = () => {
    if (isSupported.value) {
      stop()
      observer = new PerformanceObserver(callback)
      observer.observe(performanceOptions)
    }
  }

  tryOnScopeDispose(stop)

  if (immediate)
    start()

  return {
    isSupported,
    start,
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Observe performance metrics.
 *
 * @see https://vueuse.org/usePerformanceObserver
 * @param options
 */
```

- **Parameters**:
  - `options: UsePerformanceObserverOptions`
  - `callback: PerformanceObserverCallback`
- **Return Type**: `{ isSupported: any; start: () => void; stop: () => void; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `observer?.disconnect`
  - `stop`
  - `observer.observe`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `start`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    observer?.disconnect()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `observer?.disconnect`
### `start(): void`

<details><summary>Code</summary>

```ts
() => {
    if (isSupported.value) {
      stop()
      observer = new PerformanceObserver(callback)
      observer.observe(performanceOptions)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stop`
  - `observer.observe`

---

## Type Aliases

### `UsePerformanceObserverOptions`

```ts
type UsePerformanceObserverOptions = PerformanceObserverInit & ConfigurableWindow & {
  /**
   * Start the observer immediate.
   *
   * @default true
   */
  immediate?: boolean
};
```


---