[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/rxjs/useSubscription/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Unsubscribable` | `rxjs` |
| `tryOnScopeDispose` | `@vueuse/shared` |


---

## Functions

### `useSubscription(subscription: Unsubscribable): void`

<details><summary>Code</summary>

```ts
export function useSubscription(
  subscription: Unsubscribable,
) {
  tryOnScopeDispose(() => {
    subscription.unsubscribe()
  })
}
```
</details>

- **Parameters**:
  - `subscription: Unsubscribable`
- **Return Type**: `void`
- **Calls**:
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `subscription.unsubscribe`

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