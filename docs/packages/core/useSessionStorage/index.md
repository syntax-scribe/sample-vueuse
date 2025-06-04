[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 5 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useSessionStorage/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `RemovableRef` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `UseStorageOptions` | `../useStorage` |
| `defaultWindow` | `../_configurable` |
| `useStorage` | `../useStorage` |


---

## Functions

### `useSessionStorage(key: MaybeRefOrGetter<string>, initialValue: MaybeRefOrGetter<string>, options: UseStorageOptions<string>): RemovableRef<string>`

<details><summary>Code</summary>

```ts
export function useSessionStorage(key: MaybeRefOrGetter<string>, initialValue: MaybeRefOrGetter<string>, options?: UseStorageOptions<string>): RemovableRef<string>
```
</details>

- **Parameters**:
  - `key: MaybeRefOrGetter<string>`
  - `initialValue: MaybeRefOrGetter<string>`
  - `options: UseStorageOptions<string>`
- **Return Type**: `RemovableRef<string>`

---