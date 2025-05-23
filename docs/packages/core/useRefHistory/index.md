[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 7
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useRefHistory/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableEventFilter` | `@vueuse/shared` |
| `Fn` | `@vueuse/shared` |
| `Ref` | `vue` |
| `CloneFn` | `../useCloned` |
| `UseManualRefHistoryReturn` | `../useManualRefHistory` |
| `pausableFilter` | `@vueuse/shared` |
| `watchIgnorable` | `@vueuse/shared` |
| `useManualRefHistory` | `../useManualRefHistory` |


---

## Functions

### `useRefHistory(source: Ref<Raw>, options: UseRefHistoryOptions<Raw, Serialized>): UseRefHistoryReturn<Raw, Serialized>`

<details><summary>Code</summary>

```ts
export function useRefHistory<Raw, Serialized = Raw>(
  source: Ref<Raw>,
  options: UseRefHistoryOptions<Raw, Serialized> = {},
): UseRefHistoryReturn<Raw, Serialized> {
  const {
    deep = false,
    flush = 'pre',
    eventFilter,
  } = options

  const {
    eventFilter: composedFilter,
    pause,
    resume: resumeTracking,
    isActive: isTracking,
  } = pausableFilter(eventFilter)

  const {
    ignoreUpdates,
    ignorePrevAsyncUpdates,
    stop,
  } = watchIgnorable(
    source,
    commit,
    { deep, flush, eventFilter: composedFilter },
  )

  function setSource(source: Ref<Raw>, value: Raw) {
    // Support changes that are done after the last history operation
    // examples:
    //   undo, modify
    //   undo, undo, modify
    // If there were already changes in the state, they will be ignored
    // examples:
    //   modify, undo
    //   undo, modify, undo
    ignorePrevAsyncUpdates()

    ignoreUpdates(() => {
      source.value = value
    })
  }

  const manualHistory = useManualRefHistory(source, { ...options, clone: options.clone || deep, setSource })

  const { clear, commit: manualCommit } = manualHistory

  function commit() {
    // This guard only applies for flush 'pre' and 'post'
    // If the user triggers a commit manually, then reset the watcher
    // so we do not trigger an extra commit in the async watcher
    ignorePrevAsyncUpdates()

    manualCommit()
  }

  function resume(commitNow?: boolean) {
    resumeTracking()
    if (commitNow)
      commit()
  }

  function batch(fn: (cancel: Fn) => void) {
    let canceled = false

    const cancel = () => canceled = true

    ignoreUpdates(() => {
      fn(cancel)
    })

    if (!canceled)
      commit()
  }

  function dispose() {
    stop()
    clear()
  }
  return {
    ...manualHistory,
    isTracking,
    pause,
    resume,
    commit,
    batch,
    dispose,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Track the change history of a ref, also provides undo and redo functionality.
 *
 * @see https://vueuse.org/useRefHistory
 * @param source
 * @param options
 */
```

- **Parameters**:
  - `source: Ref<Raw>`
  - `options: UseRefHistoryOptions<Raw, Serialized>`
- **Return Type**: `UseRefHistoryReturn<Raw, Serialized>`
- **Calls**:
  - `pausableFilter (from @vueuse/shared)`
  - `watchIgnorable (from @vueuse/shared)`
  - `ignorePrevAsyncUpdates`
  - `ignoreUpdates`
  - `useManualRefHistory (from ../useManualRefHistory)`
  - `manualCommit`
  - `resumeTracking`
  - `commit`
  - `fn`
  - `stop`
  - `clear`
- **Internal Comments**:
```
// Support changes that are done after the last history operation (x3)
// examples: (x6)
//   undo, modify (x3)
//   undo, undo, modify (x3)
// If there were already changes in the state, they will be ignored (x3)
//   modify, undo (x3)
//   undo, modify, undo (x3)
// This guard only applies for flush 'pre' and 'post' (x3)
// If the user triggers a commit manually, then reset the watcher (x3)
// so we do not trigger an extra commit in the async watcher (x3)
```

### `setSource(source: Ref<Raw>, value: Raw): void`

<details><summary>Code</summary>

```ts
function setSource(source: Ref<Raw>, value: Raw) {
    // Support changes that are done after the last history operation
    // examples:
    //   undo, modify
    //   undo, undo, modify
    // If there were already changes in the state, they will be ignored
    // examples:
    //   modify, undo
    //   undo, modify, undo
    ignorePrevAsyncUpdates()

    ignoreUpdates(() => {
      source.value = value
    })
  }
```
</details>

- **Parameters**:
  - `source: Ref<Raw>`
  - `value: Raw`
- **Return Type**: `void`
- **Calls**:
  - `ignorePrevAsyncUpdates`
  - `ignoreUpdates`
- **Internal Comments**:
```
// Support changes that are done after the last history operation (x3)
// examples: (x6)
//   undo, modify (x3)
//   undo, undo, modify (x3)
// If there were already changes in the state, they will be ignored (x3)
//   modify, undo (x3)
//   undo, modify, undo (x3)
```

### `commit(): void`

<details><summary>Code</summary>

```ts
function commit() {
    // This guard only applies for flush 'pre' and 'post'
    // If the user triggers a commit manually, then reset the watcher
    // so we do not trigger an extra commit in the async watcher
    ignorePrevAsyncUpdates()

    manualCommit()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `ignorePrevAsyncUpdates`
  - `manualCommit`
- **Internal Comments**:
```
// This guard only applies for flush 'pre' and 'post' (x3)
// If the user triggers a commit manually, then reset the watcher (x3)
// so we do not trigger an extra commit in the async watcher (x3)
```

### `resume(commitNow: boolean): void`

<details><summary>Code</summary>

```ts
function resume(commitNow?: boolean) {
    resumeTracking()
    if (commitNow)
      commit()
  }
```
</details>

- **Parameters**:
  - `commitNow: boolean`
- **Return Type**: `void`
- **Calls**:
  - `resumeTracking`
  - `commit`
### `batch(fn: (cancel: Fn) => void): void`

<details><summary>Code</summary>

```ts
function batch(fn: (cancel: Fn) => void) {
    let canceled = false

    const cancel = () => canceled = true

    ignoreUpdates(() => {
      fn(cancel)
    })

    if (!canceled)
      commit()
  }
```
</details>

- **Parameters**:
  - `fn: (cancel: Fn) => void`
- **Return Type**: `void`
- **Calls**:
  - `ignoreUpdates`
  - `fn`
  - `commit`
### `cancel(): boolean`

<details><summary>Code</summary>

```ts
() => canceled = true
```
</details>

- **Return Type**: `boolean`
### `dispose(): void`

<details><summary>Code</summary>

```ts
function dispose() {
    stop()
    clear()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `stop`
  - `clear`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseRefHistoryOptions<Raw, Serialized = Raw>`

<details><summary>Interface Code</summary>

```ts
export interface UseRefHistoryOptions<Raw, Serialized = Raw> extends ConfigurableEventFilter {
  /**
   * Watch for deep changes, default to false
   *
   * When set to true, it will also create clones for values store in the history
   *
   * @default false
   */
  deep?: boolean

  /**
   * The flush option allows for greater control over the timing of a history point, default to 'pre'
   *
   * Possible values: 'pre', 'post', 'sync'
   * It works in the same way as the flush option in watch and watch effect in vue reactivity
   *
   * @default 'pre'
   */
  flush?: 'pre' | 'post' | 'sync'

  /**
   * Maximum number of history to be kept. Default to unlimited.
   */
  capacity?: number

  /**
   * Clone when taking a snapshot, shortcut for dump: JSON.parse(JSON.stringify(value)).
   * Default to false
   *
   * @default false
   */
  clone?: boolean | CloneFn<Raw>
  /**
   * Serialize data into the history
   */
  dump?: (v: Raw) => Serialized
  /**
   * Deserialize data from the history
   */
  parse?: (v: Serialized) => Raw
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `deep` | `boolean` | ✓ |  |
| `flush` | `'pre' | 'post' | 'sync'` | ✓ |  |
| `capacity` | `number` | ✓ |  |
| `clone` | `boolean | CloneFn<Raw>` | ✓ |  |
| `dump` | `(v: Raw) => Serialized` | ✓ |  |
| `parse` | `(v: Serialized) => Raw` | ✓ |  |

### `UseRefHistoryReturn<Raw, Serialized>`

<details><summary>Interface Code</summary>

```ts
export interface UseRefHistoryReturn<Raw, Serialized> extends UseManualRefHistoryReturn<Raw, Serialized> {
  /**
   * A ref representing if the tracking is enabled
   */
  isTracking: Ref<boolean>

  /**
   * Pause change tracking
   */
  pause: () => void

  /**
   * Resume change tracking
   *
   * @param [commit] if true, a history record will be create after resuming
   */
  resume: (commit?: boolean) => void

  /**
   * A sugar for auto pause and auto resuming within a function scope
   *
   * @param fn
   */
  batch: (fn: (cancel: Fn) => void) => void

  /**
   * Clear the data and stop the watch
   */
  dispose: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isTracking` | `Ref<boolean>` | ✗ |  |
| `pause` | `() => void` | ✗ |  |
| `resume` | `(commit?: boolean) => void` | ✗ |  |
| `batch` | `(fn: (cancel: Fn) => void) => void` | ✗ |  |
| `dispose` | `() => void` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---