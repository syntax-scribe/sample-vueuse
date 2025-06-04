[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 6 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `ignoreUpdates` | `IgnoredUpdater` | let/var | `*not shown*` | ✗ |
| `ignorePrevAsyncUpdates` | `() => void` | let/var | `*not shown*` | ✗ |
| `stop` | `() => void` | let/var | `*not shown*` | ✗ |
| `disposables` | `Fn[]` | const | `[]` | ✗ |
| `syncCounterPrev` | `any` | const | `syncCounter.value` | ✗ |
| `ignore` | `boolean` | const | `ignoreCounter.value > 0 && ignoreCounter.value === syncCounter.value` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


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