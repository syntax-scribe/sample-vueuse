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
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useDebounceFn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `DebounceFilterOptions` | `../utils` |
| `FunctionArgs` | `../utils` |
| `PromisifyFn` | `../utils` |
| `createFilterWrapper` | `../utils` |
| `debounceFilter` | `../utils` |


---

## Functions

### `useDebounceFn(fn: T, ms: MaybeRefOrGetter<number>, options: DebounceFilterOptions): UseDebounceFnReturn<T>`

<details><summary>Code</summary>

```ts
export function useDebounceFn<T extends FunctionArgs>(
  fn: T,
  ms: MaybeRefOrGetter<number> = 200,
  options: DebounceFilterOptions = {},
): UseDebounceFnReturn<T> {
  return createFilterWrapper(
    debounceFilter(ms, options),
    fn,
  )
}
```
</details>

- **JSDoc**:
```ts
/**
 * Debounce execution of a function.
 *
 * @see https://vueuse.org/useDebounceFn
 * @param  fn          A function to be executed after delay milliseconds debounced.
 * @param  ms          A zero-or-greater delay in milliseconds. For event callbacks, values around 100 or 250 (or even higher) are most useful.
 * @param  options     Options
 *
 * @return A new, debounce, function.
 */
```

- **Parameters**:
  - `fn: T`
  - `ms: MaybeRefOrGetter<number>`
  - `options: DebounceFilterOptions`
- **Return Type**: `UseDebounceFnReturn<T>`
- **Calls**:
  - `createFilterWrapper (from ../utils)`
  - `debounceFilter (from ../utils)`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseDebounceFnReturn<T extends FunctionArgs extends FunctionArgs>`

```ts
type UseDebounceFnReturn<T extends FunctionArgs extends FunctionArgs> = PromisifyFn<T>;
```


---