[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
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
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useDebouncedRefHistory/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `UseRefHistoryOptions` | `../useRefHistory` |
| `UseRefHistoryReturn` | `../useRefHistory` |
| `debounceFilter` | `@vueuse/shared` |
| `useRefHistory` | `../useRefHistory` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `filter` | `any` | const | `options.debounce ? debounceFilter(options.debounce) : undefined` | ✗ |


---

## Functions

### `useDebouncedRefHistory(source: Ref<Raw>, options: Omit<UseRefHistoryOptions<Raw, Serialized>, 'eventFilter'> & { debounce?: MaybeRefOrGetter<number> }): UseRefHistoryReturn<Raw, Serialized>`

<details><summary>Code</summary>

```ts
export function useDebouncedRefHistory<Raw, Serialized = Raw>(
  source: Ref<Raw>,
  options: Omit<UseRefHistoryOptions<Raw, Serialized>, 'eventFilter'> & { debounce?: MaybeRefOrGetter<number> } = {},
): UseRefHistoryReturn<Raw, Serialized> {
  const filter = options.debounce ? debounceFilter(options.debounce) : undefined
  const history = useRefHistory(source, { ...options, eventFilter: filter })

  return {
    ...history,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Shorthand for [useRefHistory](https://vueuse.org/useRefHistory) with debounce filter.
 *
 * @see https://vueuse.org/useDebouncedRefHistory
 * @param source
 * @param options
 */
```

- **Parameters**:
  - `source: Ref<Raw>`
  - `options: Omit<UseRefHistoryOptions<Raw, Serialized>, 'eventFilter'> & { debounce?: MaybeRefOrGetter<number> }`
- **Return Type**: `UseRefHistoryReturn<Raw, Serialized>`
- **Calls**:
  - `debounceFilter (from @vueuse/shared)`
  - `useRefHistory (from ../useRefHistory)`

---