[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 12 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

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