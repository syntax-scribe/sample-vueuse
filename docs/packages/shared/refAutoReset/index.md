[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `timer` | `any` | let/var | `*not shown*` | ✗ |


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
### `resetAfter(): Timeout`

<details><summary>Code</summary>

```ts
() =>
      setTimeout(() => {
        value = toValue(defaultValue)
        trigger()
      }, toValue(afterMs))
```
</details>

- **Return Type**: `Timeout`
- **Calls**:
  - `setTimeout`

---

## Type Aliases

### `RefAutoResetReturn<T = any = any>`

```ts
type RefAutoResetReturn<T = any = any> = Ref<T>;
```


---