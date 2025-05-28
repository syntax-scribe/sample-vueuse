[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useThrottledRefHistory/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `Ref` | `vue` |
| `UseRefHistoryOptions` | `../useRefHistory` |
| `UseRefHistoryReturn` | `../useRefHistory` |
| `throttleFilter` | `@vueuse/shared` |
| `useRefHistory` | `../useRefHistory` |


---

## Functions

### `useThrottledRefHistory(source: Ref<Raw>, options: UseThrottledRefHistoryOptions<Raw, Serialized>): UseThrottledRefHistoryReturn<Raw, Serialized>`

<details><summary>Code</summary>

```ts
export function useThrottledRefHistory<Raw, Serialized = Raw>(
  source: Ref<Raw>,
  options: UseThrottledRefHistoryOptions<Raw, Serialized> = {},
): UseThrottledRefHistoryReturn<Raw, Serialized> {
  const { throttle = 200, trailing = true } = options
  const filter = throttleFilter(throttle, trailing)
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
 * Shorthand for [useRefHistory](https://vueuse.org/useRefHistory) with throttled filter.
 *
 * @see https://vueuse.org/useThrottledRefHistory
 * @param source
 * @param options
 */
```

- **Parameters**:
  - `source: Ref<Raw>`
  - `options: UseThrottledRefHistoryOptions<Raw, Serialized>`
- **Return Type**: `UseThrottledRefHistoryReturn<Raw, Serialized>`
- **Calls**:
  - `throttleFilter (from @vueuse/shared)`
  - `useRefHistory (from ../useRefHistory)`

---

## Type Aliases

### `UseThrottledRefHistoryOptions<Raw, Serialized = Raw = Raw>`

```ts
type UseThrottledRefHistoryOptions<Raw, Serialized = Raw = Raw> = Omit<UseRefHistoryOptions<Raw, Serialized>, 'eventFilter'> & { throttle?: MaybeRef<number>, trailing?: boolean };
```

### `UseThrottledRefHistoryReturn<Raw, Serialized = Raw = Raw>`

```ts
type UseThrottledRefHistoryReturn<Raw, Serialized = Raw = Raw> = UseRefHistoryReturn<Raw, Serialized>;
```


---