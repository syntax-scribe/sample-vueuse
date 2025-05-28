[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 8 |
| 🧱 Classes | 0 |
| 📦 Imports | 1 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 3 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useMemoize/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `shallowReactive` | `vue` |


---

## Functions

### `useMemoize(resolver: (...args: Args) => Result, options: UseMemoizeOptions<Result, Args>): UseMemoizeReturn<Result, Args>`

<details><summary>Code</summary>

```ts
export function useMemoize<Result, Args extends unknown[]>(
  resolver: (...args: Args) => Result,
  options?: UseMemoizeOptions<Result, Args>,
): UseMemoizeReturn<Result, Args> {
  const initCache = (): UseMemoizeCache<CacheKey, Result> => {
    if (options?.cache)
      return shallowReactive(options.cache)
    return shallowReactive(new Map<CacheKey, Result>())
  }
  const cache = initCache()

  /**
   * Generate key from args
   */
  const generateKey = (...args: Args) => options?.getKey
    ? options.getKey(...args)
    // Default key: Serialize args
    : JSON.stringify(args)

  /**
   * Load data and save in cache
   */
  const _loadData = (key: string | number, ...args: Args): Result => {
    cache.set(key, resolver(...args))
    return cache.get(key) as Result
  }
  const loadData = (...args: Args): Result => _loadData(generateKey(...args), ...args)

  /**
   * Delete key from cache
   */
  const deleteData = (...args: Args): void => {
    cache.delete(generateKey(...args))
  }

  /**
   * Clear cached data
   */
  const clearData = () => {
    cache.clear()
  }

  const memoized: Partial<UseMemoizeReturn<Result, Args>> = (...args: Args): Result => {
    // Get data from cache
    const key = generateKey(...args)
    if (cache.has(key))
      return cache.get(key) as Result
    return _loadData(key, ...args)
  }
  memoized.load = loadData
  memoized.delete = deleteData
  memoized.clear = clearData
  memoized.generateKey = generateKey
  memoized.cache = cache

  return memoized as UseMemoizeReturn<Result, Args>
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive function result cache based on arguments
 */
```

- **Parameters**:
  - `resolver: (...args: Args) => Result`
  - `options: UseMemoizeOptions<Result, Args>`
- **Return Type**: `UseMemoizeReturn<Result, Args>`
- **Calls**:
  - `shallowReactive (from vue)`
  - `initCache`
  - `options.getKey`
  - `JSON.stringify`
  - `cache.set`
  - `resolver`
  - `cache.get`
  - `_loadData`
  - `generateKey`
  - `cache.delete`
  - `cache.clear`
  - `cache.has`
- **Internal Comments**:
```
/**
   * Generate key from args
   */ (x2)
// Default key: Serialize args
/**
   * Load data and save in cache
   */ (x2)
/**
   * Delete key from cache
   */ (x2)
/**
   * Clear cached data
   */ (x2)
// Get data from cache (x2)
```

### `initCache(): UseMemoizeCache<CacheKey, Result>`

<details><summary>Code</summary>

```ts
(): UseMemoizeCache<CacheKey, Result> => {
    if (options?.cache)
      return shallowReactive(options.cache)
    return shallowReactive(new Map<CacheKey, Result>())
  }
```
</details>

- **Return Type**: `UseMemoizeCache<CacheKey, Result>`
- **Calls**:
  - `shallowReactive (from vue)`
### `generateKey(args: Args): string | number`

<details><summary>Code</summary>

```ts
(...args: Args) => options?.getKey
    ? options.getKey(...args)
    // Default key: Serialize args
    : JSON.stringify(args)
```
</details>

- **Parameters**:
  - `args: Args`
- **Return Type**: `string | number`
### `_loadData(key: string | number, args: Args): Result`

<details><summary>Code</summary>

```ts
(key: string | number, ...args: Args): Result => {
    cache.set(key, resolver(...args))
    return cache.get(key) as Result
  }
```
</details>

- **Parameters**:
  - `key: string | number`
  - `args: Args`
- **Return Type**: `Result`
- **Calls**:
  - `cache.set`
  - `resolver`
  - `cache.get`
### `loadData(args: Args): Result`

<details><summary>Code</summary>

```ts
(...args: Args): Result => _loadData(generateKey(...args), ...args)
```
</details>

- **Parameters**:
  - `args: Args`
- **Return Type**: `Result`
- **Calls**:
  - `_loadData`
### `deleteData(args: Args): void`

<details><summary>Code</summary>

```ts
(...args: Args): void => {
    cache.delete(generateKey(...args))
  }
```
</details>

- **Parameters**:
  - `args: Args`
- **Return Type**: `void`
- **Calls**:
  - `cache.delete`
  - `generateKey`
### `clearData(): void`

<details><summary>Code</summary>

```ts
() => {
    cache.clear()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `cache.clear`
### `memoized(args: Args): Result`

<details><summary>Code</summary>

```ts
(...args: Args): Result => {
    // Get data from cache
    const key = generateKey(...args)
    if (cache.has(key))
      return cache.get(key) as Result
    return _loadData(key, ...args)
  }
```
</details>

- **Parameters**:
  - `args: Args`
- **Return Type**: `Result`
- **Calls**:
  - `generateKey`
  - `cache.has`
  - `cache.get`
  - `_loadData`
- **Internal Comments**:
```
// Get data from cache (x2)
```


---

## Interfaces

### `UseMemoizeCache<Key, Value>`

<details><summary>Interface Code</summary>

```ts
export interface UseMemoizeCache<Key, Value> {
  /**
   * Get value for key
   */
  get: (key: Key) => Value | undefined
  /**
   * Set value for key
   */
  set: (key: Key, value: Value) => void
  /**
   * Return flag if key exists
   */
  has: (key: Key) => boolean
  /**
   * Delete value for key
   */
  delete: (key: Key) => void
  /**
   * Clear cache
   */
  clear: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `get` | `(key: Key) => Value | undefined` | ✗ |  |
| `set` | `(key: Key, value: Value) => void` | ✗ |  |
| `has` | `(key: Key) => boolean` | ✗ |  |
| `delete` | `(key: Key) => void` | ✗ |  |
| `clear` | `() => void` | ✗ |  |

### `UseMemoizeReturn<Result, Args extends unknown[]>`

<details><summary>Interface Code</summary>

```ts
export interface UseMemoizeReturn<Result, Args extends unknown[]> {
  /**
   * Get result from cache or call memoized function
   */
  (...args: Args): Result
  /**
   * Call memoized function and update cache
   */
  load: (...args: Args) => Result
  /**
   * Delete cache of given arguments
   */
  delete: (...args: Args) => void
  /**
   * Clear cache
   */
  clear: () => void
  /**
   * Generate cache key for given arguments
   */
  generateKey: (...args: Args) => CacheKey
  /**
   * Cache container
   */
  cache: UseMemoizeCache<CacheKey, Result>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `load` | `(...args: Args) => Result` | ✗ |  |
| `delete` | `(...args: Args) => void` | ✗ |  |
| `clear` | `() => void` | ✗ |  |
| `generateKey` | `(...args: Args) => CacheKey` | ✗ |  |
| `cache` | `UseMemoizeCache<CacheKey, Result>` | ✗ |  |

### `UseMemoizeOptions<Result, Args extends unknown[]>`

<details><summary>Interface Code</summary>

```ts
export interface UseMemoizeOptions<Result, Args extends unknown[]> {
  getKey?: (...args: Args) => string | number
  cache?: UseMemoizeCache<CacheKey, Result>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `getKey` | `(...args: Args) => string | number` | ✓ |  |
| `cache` | `UseMemoizeCache<CacheKey, Result>` | ✓ |  |


---

## Type Aliases

### `CacheKey`

```ts
type CacheKey = any;
```


---