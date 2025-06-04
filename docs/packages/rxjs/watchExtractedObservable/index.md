[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `subscription` | `Subscription | undefined` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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