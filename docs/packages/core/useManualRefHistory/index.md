[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 12 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 3 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useManualRefHistory/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `Ref` | `vue` |
| `CloneFn` | `../useCloned` |
| `timestamp` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `markRaw` | `vue` |
| `cloneFnJSON` | `../useCloned` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `last` | `Ref<UseRefHistoryRecord<Serialized>>` | const | `deepRef(_createHistoryRecord()) as Ref<UseRefHistoryRecord<Serialized>>` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `fnBypass(v: F): T`

<details><summary>Code</summary>

```ts
function fnBypass<F, T>(v: F) {
  return v as unknown as T
}
```
</details>

- **Parameters**:
  - `v: F`
- **Return Type**: `T`
### `fnSetSource(source: Ref<F>, value: F): F`

<details><summary>Code</summary>

```ts
function fnSetSource<F>(source: Ref<F>, value: F) {
  return source.value = value
}
```
</details>

- **Parameters**:
  - `source: Ref<F>`
  - `value: F`
- **Return Type**: `F`
### `defaultDump(clone: boolean | CloneFn<R>): FnCloneOrBypass<R, S>`

<details><summary>Code</summary>

```ts
function defaultDump<R, S>(clone?: boolean | CloneFn<R>) {
  return (clone
    ? typeof clone === 'function'
      ? clone
      : cloneFnJSON
    : fnBypass
  ) as unknown as FnCloneOrBypass<R, S>
}
```
</details>

- **Parameters**:
  - `clone: boolean | CloneFn<R>`
- **Return Type**: `FnCloneOrBypass<R, S>`
### `defaultParse(clone: boolean | CloneFn<R>): FnCloneOrBypass<S, R>`

<details><summary>Code</summary>

```ts
function defaultParse<R, S>(clone?: boolean | CloneFn<R>) {
  return (clone
    ? typeof clone === 'function'
      ? clone
      : cloneFnJSON
    : fnBypass
  ) as unknown as FnCloneOrBypass<S, R>
}
```
</details>

- **Parameters**:
  - `clone: boolean | CloneFn<R>`
- **Return Type**: `FnCloneOrBypass<S, R>`
### `useManualRefHistory(source: Ref<Raw>, options: UseManualRefHistoryOptions<Raw, Serialized>): UseManualRefHistoryReturn<Raw, Serialized>`

<details><summary>Code</summary>

```ts
export function useManualRefHistory<Raw, Serialized = Raw>(
  source: Ref<Raw>,
  options: UseManualRefHistoryOptions<Raw, Serialized> = {},
): UseManualRefHistoryReturn<Raw, Serialized> {
  const {
    clone = false,
    dump = defaultDump<Raw, Serialized>(clone),
    parse = defaultParse<Raw, Serialized>(clone),
    setSource = fnSetSource,
  } = options

  function _createHistoryRecord(): UseRefHistoryRecord<Serialized> {
    return markRaw({
      snapshot: dump(source.value),
      timestamp: timestamp(),
    })
  }

  const last: Ref<UseRefHistoryRecord<Serialized>> = deepRef(_createHistoryRecord()) as Ref<UseRefHistoryRecord<Serialized>>

  const undoStack: Ref<UseRefHistoryRecord<Serialized>[]> = deepRef([])
  const redoStack: Ref<UseRefHistoryRecord<Serialized>[]> = deepRef([])

  const _setSource = (record: UseRefHistoryRecord<Serialized>) => {
    setSource(source, parse(record.snapshot))
    last.value = record
  }

  const commit = () => {
    undoStack.value.unshift(last.value)
    last.value = _createHistoryRecord()

    if (options.capacity && undoStack.value.length > options.capacity)
      undoStack.value.splice(options.capacity, Number.POSITIVE_INFINITY)
    if (redoStack.value.length)
      redoStack.value.splice(0, redoStack.value.length)
  }

  const clear = () => {
    undoStack.value.splice(0, undoStack.value.length)
    redoStack.value.splice(0, redoStack.value.length)
  }

  const undo = () => {
    const state = undoStack.value.shift()

    if (state) {
      redoStack.value.unshift(last.value)
      _setSource(state)
    }
  }

  const redo = () => {
    const state = redoStack.value.shift()

    if (state) {
      undoStack.value.unshift(last.value)
      _setSource(state)
    }
  }

  const reset = () => {
    _setSource(last.value)
  }

  const history = computed(() => [last.value, ...undoStack.value])

  const canUndo = computed(() => undoStack.value.length > 0)
  const canRedo = computed(() => redoStack.value.length > 0)

  return {
    source,
    undoStack,
    redoStack,
    last,
    history,
    canUndo,
    canRedo,

    clear,
    commit,
    reset,
    undo,
    redo,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Track the change history of a ref, also provides undo and redo functionality.
 *
 * @see https://vueuse.org/useManualRefHistory
 * @param source
 * @param options
 */
```

- **Parameters**:
  - `source: Ref<Raw>`
  - `options: UseManualRefHistoryOptions<Raw, Serialized>`
- **Return Type**: `UseManualRefHistoryReturn<Raw, Serialized>`
- **Calls**:
  - `defaultDump`
  - `defaultParse`
  - `markRaw (from vue)`
  - `dump`
  - `timestamp (from @vueuse/shared)`
  - `deepRef (from vue)`
  - `_createHistoryRecord`
  - `setSource`
  - `parse`
  - `undoStack.value.unshift`
  - `undoStack.value.splice`
  - `redoStack.value.splice`
  - `undoStack.value.shift`
  - `redoStack.value.unshift`
  - `_setSource`
  - `redoStack.value.shift`
  - `computed (from vue)`
### `_createHistoryRecord(): UseRefHistoryRecord<Serialized>`

<details><summary>Code</summary>

```ts
function _createHistoryRecord(): UseRefHistoryRecord<Serialized> {
    return markRaw({
      snapshot: dump(source.value),
      timestamp: timestamp(),
    })
  }
```
</details>

- **Return Type**: `UseRefHistoryRecord<Serialized>`
- **Calls**:
  - `markRaw (from vue)`
  - `dump`
  - `timestamp (from @vueuse/shared)`
### `_setSource(record: UseRefHistoryRecord<Serialized>): void`

<details><summary>Code</summary>

```ts
(record: UseRefHistoryRecord<Serialized>) => {
    setSource(source, parse(record.snapshot))
    last.value = record
  }
```
</details>

- **Parameters**:
  - `record: UseRefHistoryRecord<Serialized>`
- **Return Type**: `void`
- **Calls**:
  - `setSource`
  - `parse`
### `commit(): void`

<details><summary>Code</summary>

```ts
() => {
    undoStack.value.unshift(last.value)
    last.value = _createHistoryRecord()

    if (options.capacity && undoStack.value.length > options.capacity)
      undoStack.value.splice(options.capacity, Number.POSITIVE_INFINITY)
    if (redoStack.value.length)
      redoStack.value.splice(0, redoStack.value.length)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `undoStack.value.unshift`
  - `_createHistoryRecord`
  - `undoStack.value.splice`
  - `redoStack.value.splice`
### `clear(): void`

<details><summary>Code</summary>

```ts
() => {
    undoStack.value.splice(0, undoStack.value.length)
    redoStack.value.splice(0, redoStack.value.length)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `undoStack.value.splice`
  - `redoStack.value.splice`
### `undo(): void`

<details><summary>Code</summary>

```ts
() => {
    const state = undoStack.value.shift()

    if (state) {
      redoStack.value.unshift(last.value)
      _setSource(state)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `undoStack.value.shift`
  - `redoStack.value.unshift`
  - `_setSource`
### `redo(): void`

<details><summary>Code</summary>

```ts
() => {
    const state = redoStack.value.shift()

    if (state) {
      undoStack.value.unshift(last.value)
      _setSource(state)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `redoStack.value.shift`
  - `undoStack.value.unshift`
  - `_setSource`
### `reset(): void`

<details><summary>Code</summary>

```ts
() => {
    _setSource(last.value)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `_setSource`

---

## Interfaces

### `UseRefHistoryRecord<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseRefHistoryRecord<T> {
  snapshot: T
  timestamp: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `snapshot` | `T` | ✗ |  |
| `timestamp` | `number` | ✗ |  |

### `UseManualRefHistoryOptions<Raw, Serialized = Raw>`

<details><summary>Interface Code</summary>

```ts
export interface UseManualRefHistoryOptions<Raw, Serialized = Raw> {
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

  /**
   * set data source
   */
  setSource?: (source: Ref<Raw>, v: Raw) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `capacity` | `number` | ✓ |  |
| `clone` | `boolean | CloneFn<Raw>` | ✓ |  |
| `dump` | `(v: Raw) => Serialized` | ✓ |  |
| `parse` | `(v: Serialized) => Raw` | ✓ |  |
| `setSource` | `(source: Ref<Raw>, v: Raw) => void` | ✓ |  |

### `UseManualRefHistoryReturn<Raw, Serialized>`

<details><summary>Interface Code</summary>

```ts
export interface UseManualRefHistoryReturn<Raw, Serialized> {
  /**
   * Bypassed tracking ref from the argument
   */
  source: Ref<Raw>

  /**
   * An array of history records for undo, newest comes to first
   */
  history: Ref<UseRefHistoryRecord<Serialized>[]>

  /**
   * Last history point, source can be different if paused
   */
  last: Ref<UseRefHistoryRecord<Serialized>>

  /**
   * Same as {@link UseManualRefHistoryReturn.history | history}
   */
  undoStack: Ref<UseRefHistoryRecord<Serialized>[]>

  /**
   * Records array for redo
   */
  redoStack: Ref<UseRefHistoryRecord<Serialized>[]>

  /**
   * A ref representing if undo is possible (non empty undoStack)
   */
  canUndo: ComputedRef<boolean>

  /**
   * A ref representing if redo is possible (non empty redoStack)
   */
  canRedo: ComputedRef<boolean>

  /**
   * Undo changes
   */
  undo: () => void

  /**
   * Redo changes
   */
  redo: () => void

  /**
   * Clear all the history
   */
  clear: () => void

  /**
   * Create a new history record
   */
  commit: () => void

  /**
   * Reset ref's value with latest history
   */
  reset: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `source` | `Ref<Raw>` | ✗ |  |
| `history` | `Ref<UseRefHistoryRecord<Serialized>[]>` | ✗ |  |
| `last` | `Ref<UseRefHistoryRecord<Serialized>>` | ✗ |  |
| `undoStack` | `Ref<UseRefHistoryRecord<Serialized>[]>` | ✗ |  |
| `redoStack` | `Ref<UseRefHistoryRecord<Serialized>[]>` | ✗ |  |
| `canUndo` | `ComputedRef<boolean>` | ✗ |  |
| `canRedo` | `ComputedRef<boolean>` | ✗ |  |
| `undo` | `() => void` | ✗ |  |
| `redo` | `() => void` | ✗ |  |
| `clear` | `() => void` | ✗ |  |
| `commit` | `() => void` | ✗ |  |
| `reset` | `() => void` | ✗ |  |


---

## Type Aliases

### `FnCloneOrBypass<F, T>`

```ts
type FnCloneOrBypass<F, T> = (v: F) => T;
```


---