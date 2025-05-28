[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 14 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 1 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useStorageAsync/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `RemovableRef` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `StorageLikeAsync` | `../ssr-handlers` |
| `SerializerAsync` | `../useStorage` |
| `UseStorageOptions` | `../useStorage` |
| `watchWithFilter` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `getSSRHandler` | `../ssr-handlers` |
| `useEventListener` | `../useEventListener` |
| `StorageSerializers` | `../useStorage` |
| `guessSerializerType` | `../useStorage/guess` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `data` | `RemovableRef<T>` | const | `(shallow ? shallowRef : deepRef)(toValue(initialValue)) as RemovableRef<T>` | ✗ |
| `serializer` | `SerializerAsync<T>` | const | `options.serializer ?? StorageSerializers[type]` | ✗ |
| `rawValue` | `any` | let/var | `event ? event.newValue : await storage.getItem(key)` | ✗ |
| `value` | `Awaitable<T>` | let/var | `await serializer.read(rawValue)` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `read` | storage.getItem(key), storage.setItem(key, await serializer.write(rawInit)), serializer.write(rawInit), serializer.read(rawValue), serializer.read(rawValue) | *none* |


---

## Functions

### `useStorageAsync(key: string, initialValue: MaybeRefOrGetter<string>, storage: StorageLikeAsync, options: UseStorageAsyncOptions<string>): RemovableRef<string>`

<details><summary>Code</summary>

```ts
export function useStorageAsync(key: string, initialValue: MaybeRefOrGetter<string>, storage?: StorageLikeAsync, options?: UseStorageAsyncOptions<string>): RemovableRef<string>
```
</details>

- **Parameters**:
  - `key: string`
  - `initialValue: MaybeRefOrGetter<string>`
  - `storage: StorageLikeAsync`
  - `options: UseStorageAsyncOptions<string>`
- **Return Type**: `RemovableRef<string>`
### `read(event: StorageEvent): Promise<void>`

<details><summary>Code</summary>

```ts
async function read(event?: StorageEvent) {
    if (!storage || (event && event.key !== key))
      return

    try {
      const rawValue = event ? event.newValue : await storage.getItem(key)
      if (rawValue == null) {
        data.value = rawInit
        if (writeDefaults && rawInit !== null)
          await storage.setItem(key, await serializer.write(rawInit))
      }
      else if (mergeDefaults) {
        const value = await serializer.read(rawValue)
        if (typeof mergeDefaults === 'function')
          data.value = mergeDefaults(value, rawInit)
        else if (type === 'object' && !Array.isArray(value))
          data.value = { ...(rawInit as any), ...value }
        else data.value = value
      }
      else {
        data.value = await serializer.read(rawValue)
      }
    }
    catch (e) {
      onError(e)
    }
  }
```
</details>

- **Parameters**:
  - `event: StorageEvent`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `storage.getItem`
  - `storage.setItem`
  - `serializer.write`
  - `serializer.read`
  - `mergeDefaults`
  - `Array.isArray`
  - `onError`

---

## Interfaces

### `UseStorageAsyncOptions<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseStorageAsyncOptions<T> extends Omit<UseStorageOptions<T>, 'serializer'> {
  /**
   * Custom data serialization
   */
  serializer?: SerializerAsync<T>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `serializer` | `SerializerAsync<T>` | ✓ |  |


---