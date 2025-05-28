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
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/computedEager/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `WatchOptionsBase` | `vue` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `watchEffect` | `vue` |


---

## Functions

### `computedEager(fn: () => T, options: ComputedEagerOptions): ComputedEagerReturn<T>`

<details><summary>Code</summary>

```ts
export function computedEager<T>(fn: () => T, options?: ComputedEagerOptions): ComputedEagerReturn<T> {
  const result = shallowRef()

  watchEffect(() => {
    result.value = fn()
  }, {
    ...options,
    flush: options?.flush ?? 'sync',
  })

  return readonly(result)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Note: If you are using Vue 3.4+, you can straight use computed instead.
 * Because in Vue 3.4+, if computed new value does not change,
 * computed, effect, watch, watchEffect, render dependencies will not be triggered.
 * refer: https://github.com/vuejs/core/pull/5912
 *
 * @param fn effect function
 * @param options WatchOptionsBase
 * @returns readonly shallowRef
 */
```

- **Parameters**:
  - `fn: () => T`
  - `options: ComputedEagerOptions`
- **Return Type**: `ComputedEagerReturn<T>`
- **Calls**:
  - `shallowRef (from vue)`
  - `watchEffect (from vue)`
  - `fn`
  - `readonly (from vue)`

---

## Type Aliases

### `ComputedEagerOptions`

```ts
type ComputedEagerOptions = WatchOptionsBase;
```

### `ComputedEagerReturn<T = any = any>`

```ts
type ComputedEagerReturn<T = any = any> = Readonly<ShallowRef<T>>;
```


---