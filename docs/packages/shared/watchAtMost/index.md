[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 12
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/watchAtMost/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `WatchCallback` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `WatchWithFilterOptions` | `../watchWithFilter` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watchWithFilter` | `../watchWithFilter` |


---

## Functions

### `watchAtMost(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: WatchAtMostOptions<Immediate>): WatchAtMostReturn`

<details><summary>Code</summary>

```ts
export function watchAtMost<T extends Readonly<WatchSource<unknown>[]>, Immediate extends Readonly<boolean> = false>(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: WatchAtMostOptions<Immediate>): WatchAtMostReturn
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>`
  - `options: WatchAtMostOptions<Immediate>`
- **Return Type**: `WatchAtMostReturn`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `WatchAtMostOptions<Immediate>`

<details><summary>Interface Code</summary>

```ts
export interface WatchAtMostOptions<Immediate> extends WatchWithFilterOptions<Immediate> {
  count: MaybeRefOrGetter<number>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `count` | `MaybeRefOrGetter<number>` | ✗ |  |

### `WatchAtMostReturn`

<details><summary>Interface Code</summary>

```ts
export interface WatchAtMostReturn {
  stop: WatchStopHandle
  count: ShallowRef<number>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `stop` | `WatchStopHandle` | ✗ |  |
| `count` | `ShallowRef<number>` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---