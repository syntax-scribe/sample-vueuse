[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 10
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/watchWithFilter/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchCallback` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `ConfigurableEventFilter` | `../utils` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `watch` | `vue` |
| `bypassFilter` | `../utils` |
| `createFilterWrapper` | `../utils` |


---

## Functions

### `watchWithFilter(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: WatchWithFilterOptions<Immediate>): WatchStopHandle`

<details><summary>Code</summary>

```ts
export function watchWithFilter<T extends Readonly<WatchSource<unknown>[]>, Immediate extends Readonly<boolean> = false>(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options?: WatchWithFilterOptions<Immediate>): WatchStopHandle
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>`
  - `options: WatchWithFilterOptions<Immediate>`
- **Return Type**: `WatchStopHandle`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `WatchWithFilterOptions<Immediate>`

<details><summary>Interface Code</summary>

```ts
export interface WatchWithFilterOptions<Immediate> extends WatchOptions<Immediate>, ConfigurableEventFilter {}
```
</details>


---

## Type Aliases

> No type aliases found in this file.


---