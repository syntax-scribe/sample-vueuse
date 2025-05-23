[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---