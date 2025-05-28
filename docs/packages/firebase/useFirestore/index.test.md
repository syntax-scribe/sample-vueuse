[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

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
| 🟢 Vue Composition API | 4 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `dummyFirestore` | `Firestore` | const | `{} as Firestore` | ✗ |
| `data` | `any` | let/var | `*not shown*` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


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