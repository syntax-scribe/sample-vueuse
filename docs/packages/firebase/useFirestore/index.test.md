[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 15
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/firebase/useFirestore/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Firestore` | `firebase/firestore` |
| `collection` | `firebase/firestore` |
| `doc` | `firebase/firestore` |
| `afterEach` | `vitest` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `effectScope` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `useFirestore` | `./index` |


---

## Functions

### `getMockSnapFromRef(docRef: any): { id: string; data: () => any; }`

<details><summary>Code</summary>

```ts
function getMockSnapFromRef(docRef: any) {
  return {
    id: `${docRef.path}-id`,
    data: () => docRef.path === 'users/invalid' ? null : docRef,
  }
}
```
</details>

- **Parameters**:
  - `docRef: any`
- **Return Type**: `{ id: string; data: () => any; }`
### `data(): any`

<details><summary>Code</summary>

```ts
() => docRef.path === 'users/invalid' ? null : docRef
```
</details>

- **Return Type**: `any`
### `data(): any`

<details><summary>Code</summary>

```ts
() => docRef.path === 'users/invalid' ? null : docRef
```
</details>

- **Return Type**: `any`
### `getData(docRef: any): any`

<details><summary>Code</summary>

```ts
function getData(docRef: any) {
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
  - `docRef: any`
- **Return Type**: `any`
- **Calls**:
  - `docRef.data`
  - `Object.defineProperty`
  - `docRef.id.toString`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---