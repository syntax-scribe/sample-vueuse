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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---