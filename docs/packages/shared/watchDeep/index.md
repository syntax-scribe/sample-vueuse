[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 7 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/watchDeep/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchCallback` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `MapOldSources` | `../utils/types` |
| `MapSources` | `../utils/types` |
| `watch` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `watchDeep(source: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>, options: Omit<WatchOptions<Immediate>, 'deep'>): WatchStopHandle`

<details><summary>Code</summary>

```ts
export function watchDeep<
  T extends Readonly<WatchSource<unknown>[]>,
  Immediate extends Readonly<boolean> = false,
>(
  source: [...T],
  cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>,
  options?: Omit<WatchOptions<Immediate>, 'deep'>
): WatchStopHandle
```
</details>

- **Parameters**:
  - `source: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, Immediate>>`
  - `options: Omit<WatchOptions<Immediate>, 'deep'>`
- **Return Type**: `WatchStopHandle`

---