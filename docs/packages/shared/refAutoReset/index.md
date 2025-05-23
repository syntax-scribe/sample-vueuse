[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/refAutoReset/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `customRef` | `vue` |
| `toValue` | `vue` |
| `tryOnScopeDispose` | `../tryOnScopeDispose` |


---

## Functions

### `refAutoReset(defaultValue: MaybeRefOrGetter<T>, afterMs: MaybeRefOrGetter<number>): RefAutoResetReturn<T>`

<details><summary>Code</summary>

```ts
export function refAutoReset<T>(defaultValue: MaybeRefOrGetter<T>, afterMs: MaybeRefOrGetter<number> = 10000): RefAutoResetReturn<T> {
  return customRef<T>((track, trigger) => {
    let value: T = toValue(defaultValue)
    let timer: any

    const resetAfter = () =>
      setTimeout(() => {
        value = toValue(defaultValue)
        trigger()
      }, toValue(afterMs))

    tryOnScopeDispose(() => {
      clearTimeout(timer)
    })

    return {
      get() {
        track()
        return value
      },
      set(newValue) {
        value = newValue
        trigger()

        clearTimeout(timer)
        timer = resetAfter()
      },
    }
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create a ref which will be reset to the default value after some time.
 *
 * @see https://vueuse.org/refAutoReset
 * @param defaultValue The value which will be set.
 * @param afterMs      A zero-or-greater delay in milliseconds.
 */
```

- **Parameters**:
  - `defaultValue: MaybeRefOrGetter<T>`
  - `afterMs: MaybeRefOrGetter<number>`
- **Return Type**: `RefAutoResetReturn<T>`
- **Calls**:
  - `customRef (from vue)`
  - `toValue (from vue)`
  - `setTimeout`
  - `trigger`
  - `tryOnScopeDispose (from ../tryOnScopeDispose)`
  - `clearTimeout`
  - `track`
  - `resetAfter`
### `resetAfter(): number`

<details><summary>Code</summary>

```ts
() =>
      setTimeout(() => {
        value = toValue(defaultValue)
        trigger()
      }, toValue(afterMs))
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `setTimeout`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `RefAutoResetReturn<T = any = any>`

```ts
type RefAutoResetReturn<T = any = any> = Ref<T>;
```


---