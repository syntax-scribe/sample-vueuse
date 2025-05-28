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
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Type Aliases

### `UseDebounceFnReturn<T extends FunctionArgs extends FunctionArgs>`

```ts
type UseDebounceFnReturn<T extends FunctionArgs extends FunctionArgs> = PromisifyFn<T>;
```


---