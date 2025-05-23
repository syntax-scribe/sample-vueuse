[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 2

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


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