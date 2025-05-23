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
- **Imports**: 10
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/watchPausable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchCallback` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `Pausable` | `../utils` |
| `PausableFilterOptions` | `../utils` |
| `WatchWithFilterOptions` | `../watchWithFilter` |
| `pausableFilter` | `../utils` |
| `watchWithFilter` | `../watchWithFilter` |


---

## Functions

### `watchPausable(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: WatchPausableOptions<Immediate>): WatchPausableReturn`

<details><summary>Code</summary>

```ts
export function watchPausable<T extends Readonly<WatchSource<unknown>[]>, Immediate extends Readonly<boolean> = false>(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options?: WatchPausableOptions<Immediate>): WatchPausableReturn
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>`
  - `options: WatchPausableOptions<Immediate>`
- **Return Type**: `WatchPausableReturn`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `WatchPausableReturn`

<details><summary>Interface Code</summary>

```ts
export interface WatchPausableReturn extends Pausable {
  stop: WatchStopHandle
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `stop` | `WatchStopHandle` | ✗ |  |


---

## Type Aliases

### `WatchPausableOptions<Immediate>`

```ts
type WatchPausableOptions<Immediate> = WatchWithFilterOptions<Immediate> & PausableFilterOptions;
```


---