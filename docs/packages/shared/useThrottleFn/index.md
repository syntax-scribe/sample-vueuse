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
📂 **`packages/shared/useThrottleFn/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `FunctionArgs` | `../utils` |
| `PromisifyFn` | `../utils` |
| `createFilterWrapper` | `../utils` |
| `throttleFilter` | `../utils` |


---

## Functions

### `useThrottleFn(fn: T, ms: MaybeRefOrGetter<number>, trailing: boolean, leading: boolean, rejectOnCancel: boolean): PromisifyFn<T>`

<details><summary>Code</summary>

```ts
export function useThrottleFn<T extends FunctionArgs>(
  fn: T,
  ms: MaybeRefOrGetter<number> = 200,
  trailing = false,
  leading = true,
  rejectOnCancel = false,
): PromisifyFn<T> {
  return createFilterWrapper(
    throttleFilter(ms, trailing, leading, rejectOnCancel),
    fn,
  )
}
```
</details>

- **JSDoc**:
```ts
/**
 * Throttle execution of a function. Especially useful for rate limiting
 * execution of handlers on events like resize and scroll.
 *
 * @param   fn             A function to be executed after delay milliseconds. The `this` context and all arguments are passed through, as-is,
 *                                    to `callback` when the throttled-function is executed.
 * @param   ms             A zero-or-greater delay in milliseconds. For event callbacks, values around 100 or 250 (or even higher) are most useful.
 *                                    (default value: 200)
 *
 * @param [trailing] if true, call fn again after the time is up (default value: false)
 *
 * @param [leading] if true, call fn on the leading edge of the ms timeout (default value: true)
 *
 * @param [rejectOnCancel] if true, reject the last call if it's been cancel (default value: false)
 *
 * @return  A new, throttled, function.
 */
```

- **Parameters**:
  - `fn: T`
  - `ms: MaybeRefOrGetter<number>`
  - `trailing: boolean`
  - `leading: boolean`
  - `rejectOnCancel: boolean`
- **Return Type**: `PromisifyFn<T>`
- **Calls**:
  - `createFilterWrapper (from ../utils)`
  - `throttleFilter (from ../utils)`

---