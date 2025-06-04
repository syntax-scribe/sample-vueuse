[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 6 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/firebase/useAuth/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Auth` | `firebase/auth` |
| `User` | `firebase/auth` |
| `ComputedRef` | `vue` |
| `Ref` | `vue` |
| `computed` | `vue` |
| `deepRef` | `vue` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `useAuth(auth: Auth): { isAuthenticated: any; user: any; }`

<details><summary>Code</summary>

```ts
export function useAuth(auth: Auth) {
  const user = deepRef<User | null>(auth.currentUser)
  const isAuthenticated = computed(() => !!user.value)

  auth.onIdTokenChanged(authUser => user.value = authUser)

  return {
    isAuthenticated,
    user,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Firebase Auth binding
 *
 * @see https://vueuse.org/useAuth
 */
```

- **Parameters**:
  - `auth: Auth`
- **Return Type**: `{ isAuthenticated: any; user: any; }`
- **Calls**:
  - `deepRef (from vue)`
  - `computed (from vue)`
  - `auth.onIdTokenChanged`

---

## Interfaces

### `UseFirebaseAuthOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFirebaseAuthOptions {
  isAuthenticated: ComputedRef<boolean>
  user: Ref<User | null>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isAuthenticated` | `ComputedRef<boolean>` | ✗ |  |
| `user` | `Ref<User | null>` | ✗ |  |


---