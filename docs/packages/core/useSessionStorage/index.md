[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
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