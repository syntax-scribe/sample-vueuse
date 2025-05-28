[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/watchDebounced/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `WatchCallback` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `DebounceFilterOptions` | `../utils` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `debounceFilter` | `../utils` |
| `watchWithFilter` | `../watchWithFilter` |


---

## Functions

### `watchDebounced(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: WatchDebouncedOptions<Immediate>): WatchStopHandle`

<details><summary>Code</summary>

```ts
export function watchDebounced<T extends Readonly<WatchSource<unknown>[]>, Immediate extends Readonly<boolean> = false>(sources: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options?: WatchDebouncedOptions<Immediate>): WatchStopHandle
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>`
  - `options: WatchDebouncedOptions<Immediate>`
- **Return Type**: `WatchStopHandle`

---

## Interfaces

### `WatchDebouncedOptions<Immediate>`

<details><summary>Interface Code</summary>

```ts
export interface WatchDebouncedOptions<Immediate> extends WatchOptions<Immediate>, DebounceFilterOptions {
  debounce?: MaybeRefOrGetter<number>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `debounce` | `MaybeRefOrGetter<number>` | ✓ |  |


---