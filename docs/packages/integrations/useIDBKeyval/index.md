[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 14 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 4 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/integrations/useIDBKeyval/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableFlush` | `@vueuse/shared` |
| `RemovableRef` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `watchPausable` | `@vueuse/core` |
| `del` | `idb-keyval` |
| `get` | `idb-keyval` |
| `set` | `idb-keyval` |
| `update` | `idb-keyval` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `toRaw` | `vue` |
| `toValue` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `data` | `Ref<T>` | const | `(shallow ? shallowRef : deepRef)(initialValue) as Ref<T>` | ✗ |
| `rawValue` | `any` | let/var | `await get<T>(key)` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useIDBKeyval` | get<T>(key), set(key, rawInit), del(key), update(key, () => toRaw(data.value)), write() | *none* |
| async-function | `read` | get<T>(key), set(key, rawInit) | *none* |
| async-function | `write` | del(key), update(key, () => toRaw(data.value)) | *none* |
| async-function | `setData` | write() | *none* |


---

## Functions

### `useIDBKeyval(key: IDBValidKey, initialValue: MaybeRefOrGetter<T>, options: UseIDBOptions): UseIDBKeyvalReturn<T>`

<details><summary>Code</summary>

```ts
export function useIDBKeyval<T>(
  key: IDBValidKey,
  initialValue: MaybeRefOrGetter<T>,
  options: UseIDBOptions = {},
): UseIDBKeyvalReturn<T> {
  const {
    flush = 'pre',
    deep = true,
    shallow = false,
    onError = (e) => {
      console.error(e)
    },
    writeDefaults = true,
  } = options

  const isFinished = shallowRef(false)
  const data = (shallow ? shallowRef : deepRef)(initialValue) as Ref<T>

  const rawInit: T = toValue(initialValue)

  async function read() {
    try {
      const rawValue = await get<T>(key)
      if (rawValue === undefined) {
        if (rawInit !== undefined && rawInit !== null && writeDefaults)
          await set(key, rawInit)
      }
      else {
        data.value = rawValue
      }
    }
    catch (e) {
      onError(e)
    }
    isFinished.value = true
  }

  read()

  async function write() {
    try {
      if (data.value == null) {
        await del(key)
      }
      else {
        // IndexedDB does not support saving proxies, convert from proxy before saving
        await update(key, () => toRaw(data.value))
      }
    }
    catch (e) {
      onError(e)
    }
  }

  const {
    pause: pauseWatch,
    resume: resumeWatch,
  } = watchPausable(data, () => write(), { flush, deep })

  async function setData(value: T): Promise<void> {
    pauseWatch()
    data.value = value
    await write()
    resumeWatch()
  }

  return {
    set: setData,
    isFinished,
    data: data as RemovableRef<T>,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 *
 * @param key
 * @param initialValue
 * @param options
 */
```

- **Parameters**:
  - `key: IDBValidKey`
  - `initialValue: MaybeRefOrGetter<T>`
  - `options: UseIDBOptions`
- **Return Type**: `UseIDBKeyvalReturn<T>`
- **Calls**:
  - `console.error`
  - `shallowRef (from vue)`
  - `complex_call_1343`
  - `toValue (from vue)`
  - `get (from idb-keyval)`
  - `set (from idb-keyval)`
  - `onError`
  - `read`
  - `del (from idb-keyval)`
  - `update (from idb-keyval)`
  - `toRaw (from vue)`
  - `watchPausable (from @vueuse/core)`
  - `write`
  - `pauseWatch`
  - `resumeWatch`
- **Internal Comments**:
```
// IndexedDB does not support saving proxies, convert from proxy before saving (x2)
```

### `read(): Promise<void>`

<details><summary>Code</summary>

```ts
async function read() {
    try {
      const rawValue = await get<T>(key)
      if (rawValue === undefined) {
        if (rawInit !== undefined && rawInit !== null && writeDefaults)
          await set(key, rawInit)
      }
      else {
        data.value = rawValue
      }
    }
    catch (e) {
      onError(e)
    }
    isFinished.value = true
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `get (from idb-keyval)`
  - `set (from idb-keyval)`
  - `onError`
### `write(): Promise<void>`

<details><summary>Code</summary>

```ts
async function write() {
    try {
      if (data.value == null) {
        await del(key)
      }
      else {
        // IndexedDB does not support saving proxies, convert from proxy before saving
        await update(key, () => toRaw(data.value))
      }
    }
    catch (e) {
      onError(e)
    }
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `del (from idb-keyval)`
  - `update (from idb-keyval)`
  - `toRaw (from vue)`
  - `onError`
- **Internal Comments**:
```
// IndexedDB does not support saving proxies, convert from proxy before saving (x2)
```

### `setData(value: T): Promise<void>`

<details><summary>Code</summary>

```ts
async function setData(value: T): Promise<void> {
    pauseWatch()
    data.value = value
    await write()
    resumeWatch()
  }
```
</details>

- **Parameters**:
  - `value: T`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `pauseWatch`
  - `write`
  - `resumeWatch`

---

## Interfaces

### `UseIDBOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseIDBOptions extends ConfigurableFlush {
  /**
   * Watch for deep changes
   *
   * @default true
   */
  deep?: boolean

  /**
   * On error callback
   *
   * Default log error to `console.error`
   */
  onError?: (error: unknown) => void

  /**
   * Use shallow ref as reference
   *
   * @default false
   */
  shallow?: boolean
  /**
   * Write the default value to the storage when it does not exist
   *
   * @default true
   */
  writeDefaults?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `deep` | `boolean` | ✓ |  |
| `onError` | `(error: unknown) => void` | ✓ |  |
| `shallow` | `boolean` | ✓ |  |
| `writeDefaults` | `boolean` | ✓ |  |

### `UseIDBKeyvalReturn<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseIDBKeyvalReturn<T> {
  data: RemovableRef<T>
  isFinished: ShallowRef<boolean>
  set: (value: T) => Promise<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `data` | `RemovableRef<T>` | ✗ |  |
| `isFinished` | `ShallowRef<boolean>` | ✗ |  |
| `set` | `(value: T) => Promise<void>` | ✗ |  |


---