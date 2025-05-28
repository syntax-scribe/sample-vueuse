[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 15 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/firebase/useFirestore/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `DocumentData` | `firebase/firestore` |
| `DocumentReference` | `firebase/firestore` |
| `DocumentSnapshot` | `firebase/firestore` |
| `Query` | `firebase/firestore` |
| `QueryDocumentSnapshot` | `firebase/firestore` |
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `isDef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `useTimeoutFn` | `@vueuse/shared` |
| `onSnapshot` | `firebase/firestore` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `isRef` | `vue` |
| `watch` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `refOfDocRef` | `any` | const | `isRef(maybeDocRef)
    ? maybeDocRef
    : computed(() => maybeDocRef)` | ✗ |
| `data` | `Ref<T | T[]>` | const | `deepRef(initialValue) as Ref<T | T[] | null | undefined>` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `getData(docRef: DocumentSnapshot<T> | QueryDocumentSnapshot<T>): any`

<details><summary>Code</summary>

```ts
function getData<T>(
  docRef: DocumentSnapshot<T> | QueryDocumentSnapshot<T>,
) {
  const data = docRef.data()

  if (data) {
    Object.defineProperty(data, 'id', {
      value: docRef.id.toString(),
      writable: false,
    })
  }

  return data
}
```
</details>

- **Parameters**:
  - `docRef: DocumentSnapshot<T> | QueryDocumentSnapshot<T>`
- **Return Type**: `any`
- **Calls**:
  - `docRef.data`
  - `Object.defineProperty`
  - `docRef.id.toString`
### `isDocumentReference(docRef: any): docRef is DocumentReference<T>`

<details><summary>Code</summary>

```ts
function isDocumentReference<T>(docRef: any): docRef is DocumentReference<T> {
  return (docRef.path?.match(/\//g) || []).length % 2 !== 0
}
```
</details>

- **Parameters**:
  - `docRef: any`
- **Return Type**: `docRef is DocumentReference<T>`
- **Calls**:
  - `docRef.path?.match`
### `useFirestore(maybeDocRef: MaybeRef<DocumentReference<T> | Falsy>, initialValue: T, options: UseFirestoreOptions): Ref<T | null>`

<details><summary>Code</summary>

```ts
export function useFirestore<T extends DocumentData>(
  maybeDocRef: MaybeRef<DocumentReference<T> | Falsy>,
  initialValue: T,
  options?: UseFirestoreOptions
): Ref<T | null>
```
</details>

- **Parameters**:
  - `maybeDocRef: MaybeRef<DocumentReference<T> | Falsy>`
  - `initialValue: T`
  - `options: UseFirestoreOptions`
- **Return Type**: `Ref<T | null>`
### `close(): void`

<details><summary>Code</summary>

```ts
() => { }
```
</details>

- **Return Type**: `void`

---

## Interfaces

### `UseFirestoreOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFirestoreOptions {
  errorHandler?: (err: Error) => void
  autoDispose?: boolean | number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `errorHandler` | `(err: Error) => void` | ✓ |  |
| `autoDispose` | `boolean | number` | ✓ |  |


---

## Type Aliases

### `FirebaseDocRef<T>`

```ts
type FirebaseDocRef<T> = Query<T> |
  DocumentReference<T>;
```

### `Falsy`

```ts
type Falsy = false | 0 | '' | null | undefined;
```


---