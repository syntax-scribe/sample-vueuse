[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 7 |
| 📦 Imports | 13 |
| 📊 Variables & Constants | 1 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/rxjs/useExtractedObservable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MapOldSources` | `@vueuse/shared` |
| `MapSources` | `@vueuse/shared` |
| `MultiWatchSources` | `@vueuse/shared` |
| `Subscription` | `rxjs` |
| `ShallowRef` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `UseObservableOptions` | `../useObservable` |
| `WatchExtractedObservableCallback` | `../watchExtractedObservable` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
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

### `useExtractedObservable(sources: [...T], extractor: WatchExtractedObservableCallback<
    MapSources<T>,
    MapOldSources<T, Immediate>,
    E
  >, options: UseExtractedObservableOptions<E>, watchOptions: WatchOptions<Immediate>): Readonly<ShallowRef<E>>`

<details><summary>Code</summary>

```ts
export function useExtractedObservable<
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
  options?: UseExtractedObservableOptions<E>,
  watchOptions?: WatchOptions<Immediate>,
): Readonly<ShallowRef<E>>
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `extractor: WatchExtractedObservableCallback<
    MapSources<T>,
    MapOldSources<T, Immediate>,
    E
  >`
  - `options: UseExtractedObservableOptions<E>`
  - `watchOptions: WatchOptions<Immediate>`
- **Return Type**: `Readonly<ShallowRef<E>>`
### `error(err: any): void`

<details><summary>Code</summary>

```ts
(err) => {
          options?.onError?.(err)
        }
```
</details>

- **Parameters**:
  - `err: any`
- **Return Type**: `void`
- **Calls**:
  - `options?.onError`
### `complete(): void`

<details><summary>Code</summary>

```ts
() => {
          options?.onComplete?.()
        }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `options?.onComplete`
### `next(val: any): void`

<details><summary>Code</summary>

```ts
(val) => {
          obsRef.value = val
        }
```
</details>

- **Parameters**:
  - `val: any`
- **Return Type**: `void`
### `error(err: any): void`

<details><summary>Code</summary>

```ts
(err) => {
          options?.onError?.(err)
        }
```
</details>

- **Parameters**:
  - `err: any`
- **Return Type**: `void`
- **Calls**:
  - `options?.onError`
### `complete(): void`

<details><summary>Code</summary>

```ts
() => {
          options?.onComplete?.()
        }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `options?.onComplete`
### `next(val: any): void`

<details><summary>Code</summary>

```ts
(val) => {
          obsRef.value = val
        }
```
</details>

- **Parameters**:
  - `val: any`
- **Return Type**: `void`

---

## Interfaces

### `UseExtractedObservableOptions<E>`

<details><summary>Interface Code</summary>

```ts
export interface UseExtractedObservableOptions<E> extends UseObservableOptions<E> {
  onComplete?: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `onComplete` | `() => void` | ✓ |  |


---