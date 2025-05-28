[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 7 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/watchTriggerable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchSource` | `vue` |
| `MapOldSources` | `../utils` |
| `MapSources` | `../utils` |
| `WatchIgnorableReturn` | `../watchIgnorable` |
| `WatchWithFilterOptions` | `../watchWithFilter` |
| `isReactive` | `vue` |
| `toValue` | `vue` |
| `watchIgnorable` | `../watchIgnorable` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `cleanupFn` | `(() => void) | undefined` | let/var | `*not shown*` | ✗ |
| `fn` | `() => void` | const | `cleanupFn` | ✗ |
| `res` | `any` | let/var | `*not shown*` | ✗ |


---

## Functions

### `watchTriggerable(sources: [...T], cb: WatchTriggerableCallback<MapSources<T>, MapOldSources<T, true>, FnReturnT>, options: WatchWithFilterOptions<boolean>): WatchTriggerableReturn<FnReturnT>`

<details><summary>Code</summary>

```ts
export function watchTriggerable<T extends Readonly<WatchSource<unknown>[]>, FnReturnT>(sources: [...T], cb: WatchTriggerableCallback<MapSources<T>, MapOldSources<T, true>, FnReturnT>, options?: WatchWithFilterOptions<boolean>): WatchTriggerableReturn<FnReturnT>
```
</details>

- **Parameters**:
  - `sources: [...T]`
  - `cb: WatchTriggerableCallback<MapSources<T>, MapOldSources<T, true>, FnReturnT>`
  - `options: WatchWithFilterOptions<boolean>`
- **Return Type**: `WatchTriggerableReturn<FnReturnT>`
### `onEffect(): void`

<details><summary>Code</summary>

```ts
function onEffect() {
    if (!cleanupFn)
      return

    const fn = cleanupFn
    cleanupFn = undefined
    fn()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `fn`
### `onCleanup(callback: () => void): void`

<details><summary>Code</summary>

```ts
function onCleanup(callback: () => void) {
    cleanupFn = callback
  }
```
</details>

- **JSDoc**:
```ts
/** Register the function `cleanupFn` */
```

- **Parameters**:
  - `callback: () => void`
- **Return Type**: `void`
### `_cb(value: any, oldValue: any): any`

<details><summary>Code</summary>

```ts
(
    value: any,
    oldValue: any,
  ) => {
    // When a new side effect occurs, clean up the previous side effect
    onEffect()

    return cb(value, oldValue, onCleanup)
  }
```
</details>

- **Parameters**:
  - `value: any`
  - `oldValue: any`
- **Return Type**: `any`
- **Calls**:
  - `onEffect`
  - `cb`
- **Internal Comments**:
```
// When a new side effect occurs, clean up the previous side effect (x3)
```

### `trigger(): any`

<details><summary>Code</summary>

```ts
() => {
    let res: any
    ignoreUpdates(() => {
      res = _cb(getWatchSources(source), getOldValue(source))
    })
    return res
  }
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `ignoreUpdates`
  - `_cb`
  - `getWatchSources`
  - `getOldValue`
### `getWatchSources(sources: any): any`

<details><summary>Code</summary>

```ts
function getWatchSources(sources: any) {
  if (isReactive(sources))
    return sources
  if (Array.isArray(sources))
    return sources.map(item => toValue(item))
  return toValue(sources)
}
```
</details>

- **Parameters**:
  - `sources: any`
- **Return Type**: `any`
- **Calls**:
  - `isReactive (from vue)`
  - `Array.isArray`
  - `sources.map`
  - `toValue (from vue)`
### `getOldValue(source: any): any[]`

<details><summary>Code</summary>

```ts
function getOldValue(source: any) {
  return Array.isArray(source)
    ? source.map(() => undefined)
    : undefined
}
```
</details>

- **Parameters**:
  - `source: any`
- **Return Type**: `any[]`
- **Calls**:
  - `Array.isArray`
  - `source.map`

---

## Interfaces

### `WatchTriggerableReturn<FnReturnT = void>`

<details><summary>Interface Code</summary>

```ts
export interface WatchTriggerableReturn<FnReturnT = void> extends WatchIgnorableReturn {
  /** Execute `WatchCallback` immediately */
  trigger: () => FnReturnT
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `trigger` | `() => FnReturnT` | ✗ |  |


---

## Type Aliases

### `OnCleanup`

```ts
type OnCleanup = (cleanupFn: () => void) => void;
```

### `WatchTriggerableCallback<V = any = any, OV = any = any, R = void = void>`

```ts
type WatchTriggerableCallback<V = any = any, OV = any = any, R = void = void> = (value: V, oldValue: OV, onCleanup: OnCleanup) => R;
```


---