[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---