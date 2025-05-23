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
- **Imports**: 11
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/watchIgnorable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchCallback` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `Fn` | `../utils` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `WatchWithFilterOptions` | `../watchWithFilter` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `bypassFilter` | `../utils` |
| `createFilterWrapper` | `../utils` |


---

## Functions

### `watchIgnorable(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: WatchWithFilterOptions<Immediate>): WatchIgnorableReturn`

<details><summary>Code</summary>

```ts
export function watchIgnorable<T extends Readonly<WatchSource<unknown>[]>, Immediate extends Readonly<boolean> = false>(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options?: WatchWithFilterOptions<Immediate>): WatchIgnorableReturn
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>`
  - `options: WatchWithFilterOptions<Immediate>`
- **Return Type**: `WatchIgnorableReturn`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `WatchIgnorableReturn`

<details><summary>Interface Code</summary>

```ts
export interface WatchIgnorableReturn {
  ignoreUpdates: IgnoredUpdater
  ignorePrevAsyncUpdates: () => void
  stop: WatchStopHandle
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `ignoreUpdates` | `IgnoredUpdater` | ✗ |  |
| `ignorePrevAsyncUpdates` | `() => void` | ✗ |  |
| `stop` | `WatchStopHandle` | ✗ |  |


---

## Type Aliases

### `IgnoredUpdater`

```ts
type IgnoredUpdater = (updater: () => void) => void;
```


---