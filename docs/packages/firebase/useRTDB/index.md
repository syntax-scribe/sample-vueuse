[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/firebase/useRTDB/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `DatabaseReference` | `firebase/database` |
| `DataSnapshot` | `firebase/database` |
| `Ref` | `vue` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `onValue` | `firebase/database` |
| `deepRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `data` | `Ref<T>` | const | `deepRef(undefined) as Ref<T | undefined>` | ✗ |


---

## Functions

### `useRTDB(docRef: DatabaseReference, options: UseRTDBOptions): Ref<T>`

<details><summary>Code</summary>

```ts
export function useRTDB<T = any>(
  docRef: DatabaseReference,
  options: UseRTDBOptions = {},
) {
  const {
    errorHandler = (err: Error) => console.error(err),
    autoDispose = true,
  } = options
  const data = deepRef(undefined) as Ref<T | undefined>

  function update(snapshot: DataSnapshot) {
    data.value = snapshot.val()
  }

  const off = onValue(docRef, update, errorHandler)

  if (autoDispose)
    tryOnScopeDispose(() => off())

  return data
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Firebase Realtime Database binding.
 *
 * @see https://vueuse.org/useRTDB
 */
```

- **Parameters**:
  - `docRef: DatabaseReference`
  - `options: UseRTDBOptions`
- **Return Type**: `Ref<T>`
- **Calls**:
  - `console.error`
  - `deepRef (from vue)`
  - `snapshot.val`
  - `onValue (from firebase/database)`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `off`
### `update(snapshot: DataSnapshot): void`

<details><summary>Code</summary>

```ts
function update(snapshot: DataSnapshot) {
    data.value = snapshot.val()
  }
```
</details>

- **Parameters**:
  - `snapshot: DataSnapshot`
- **Return Type**: `void`
- **Calls**:
  - `snapshot.val`

---

## Interfaces

### `UseRTDBOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseRTDBOptions {
  errorHandler?: (err: Error) => void
  autoDispose?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `errorHandler` | `(err: Error) => void` | ✓ |  |
| `autoDispose` | `boolean` | ✓ |  |


---