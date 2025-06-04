[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 9 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/watchThrottled/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `WatchCallback` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `throttleFilter` | `../utils` |
| `watchWithFilter` | `../watchWithFilter` |


---

## Functions

### `watchThrottled(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: WatchThrottledOptions<Immediate>): WatchStopHandle`

<details><summary>Code</summary>

```ts
export function watchThrottled<T extends Readonly<WatchSource<unknown>[]>, Immediate extends Readonly<boolean> = false>(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options?: WatchThrottledOptions<Immediate>): WatchStopHandle
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>`
  - `options: WatchThrottledOptions<Immediate>`
- **Return Type**: `WatchStopHandle`

---

## Interfaces

### `WatchThrottledOptions<Immediate>`

<details><summary>Interface Code</summary>

```ts
export interface WatchThrottledOptions<Immediate> extends WatchOptions<Immediate> {
  throttle?: MaybeRefOrGetter<number>
  trailing?: boolean
  leading?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `throttle` | `MaybeRefOrGetter<number>` | ✓ |  |
| `trailing` | `boolean` | ✓ |  |
| `leading` | `boolean` | ✓ |  |


---