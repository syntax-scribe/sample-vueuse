[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 2 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

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