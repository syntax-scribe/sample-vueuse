[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 0
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---