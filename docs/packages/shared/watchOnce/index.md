[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/watchOnce/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchCallback` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `watch` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `watchOnce(source: [...T], cb: WatchCallback<MapSources<T>, MapOldSources<T, true>>, options: Omit<WatchOptions<true>, 'once'>): WatchStopHandle`

<details><summary>Code</summary>

```ts
export function watchOnce<T extends Readonly<WatchSource<unknown>[]>>(
  source: [...T],
  cb: WatchCallback<MapSources<T>, MapOldSources<T, true>>,
  options?: Omit<WatchOptions<true>, 'once'>
): WatchStopHandle
```
</details>

- **Parameters**:
  - `source: [...T]`
  - `cb: WatchCallback<MapSources<T>, MapOldSources<T, true>>`
  - `options: Omit<WatchOptions<true>, 'once'>`
- **Return Type**: `WatchStopHandle`

---