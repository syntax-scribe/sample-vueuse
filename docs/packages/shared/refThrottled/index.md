[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/refThrottled/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `deepRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `useThrottleFn` | `../useThrottleFn` |


---

## Functions

### `refThrottled(value: Ref<T>, delay: number, trailing: boolean, leading: boolean): RefThrottledReturn<T>`

<details><summary>Code</summary>

```ts
export function refThrottled<T = any>(value: Ref<T>, delay = 200, trailing = true, leading = true): RefThrottledReturn<T> {
  if (delay <= 0)
    return value

  const throttled = deepRef(toValue(value))

  const updater = useThrottleFn(() => {
    throttled.value = value.value
  }, delay, trailing, leading)

  watch(value, () => updater())

  return throttled as Ref<T>
}
```
</details>

- **JSDoc**:
```ts
/**
 * Throttle execution of a function. Especially useful for rate limiting
 * execution of handlers on events like resize and scroll.
 *
 * @param value Ref value to be watched with throttle effect
 * @param  delay  A zero-or-greater delay in milliseconds. For event callbacks, values around 100 or 250 (or even higher) are most useful.
 * @param trailing if true, update the value again after the delay time is up
 * @param leading if true, update the value on the leading edge of the ms timeout
 */
```

- **Parameters**:
  - `value: Ref<T>`
  - `delay: number`
  - `trailing: boolean`
  - `leading: boolean`
- **Return Type**: `RefThrottledReturn<T>`
- **Calls**:
  - `deepRef (from vue)`
  - `toValue (from vue)`
  - `useThrottleFn (from ../useThrottleFn)`
  - `watch (from vue)`
  - `updater`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `RefThrottledReturn<T = any = any>`

```ts
type RefThrottledReturn<T = any = any> = Ref<T>;
```


---