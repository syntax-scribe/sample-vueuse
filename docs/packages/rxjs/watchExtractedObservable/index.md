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
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/rxjs/watchExtractedObservable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MapOldSources` | `@vueuse/shared` |
| `MapSources` | `@vueuse/shared` |
| `MultiWatchSources` | `@vueuse/shared` |
| `Observable` | `rxjs` |
| `Subscription` | `rxjs` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `WatchStopHandle` | `vue` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `watch` | `vue` |


---

## Functions

### `watchExtractedObservable(sources: [...T], extractor: WatchExtractedObservableCallback<
    MapSources<T>,
    MapOldSources<T, Immediate>,
    E
  >, callback: (snapshot: E) => void, subscriptionOptions: WatchExtractedObservableOptions, watchOptions: WatchOptions<Immediate>): WatchStopHandle`

<details><summary>Code</summary>

```ts
export function watchExtractedObservable<
  T extends MultiWatchSources,
  E,
  Immediate extends Readonly<boolean> = false,
>(
  sources: [...T],
  extractor: WatchExtractedObservableCallback<
    MapSources<T>,
    MapOldSources<T, Immediate>,
    E
  >,
  callback: (snapshot: E) => void,
  subscriptionOptions?: WatchExtractedObservableOptions,
  watchOptions?: WatchOptions<Immediate>
): WatchStopHandle
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `extractor: WatchExtractedObservableCallback<
    MapSources<T>,
    MapOldSources<T, Immediate>,
    E
  >`
  - `callback: (snapshot: E) => void`
  - `subscriptionOptions: WatchExtractedObservableOptions`
  - `watchOptions: WatchOptions<Immediate>`
- **Return Type**: `WatchStopHandle`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `WatchExtractedObservableOptions`

<details><summary>Interface Code</summary>

```ts
export interface WatchExtractedObservableOptions {
  onError?: (err: unknown) => void
  onComplete?: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `onError` | `(err: unknown) => void` | ✓ |  |
| `onComplete` | `() => void` | ✓ |  |


---

## Type Aliases

### `OnCleanup`

```ts
type OnCleanup = (cleanupFn: () => void) => void;
```

### `WatchExtractedObservableCallback<Value, OldValue, ObservableElement>`

```ts
type WatchExtractedObservableCallback<Value, OldValue, ObservableElement> = (value: NonNullable<Value>, oldValue: OldValue, onCleanup: OnCleanup) => Observable<ObservableElement>;
```


---