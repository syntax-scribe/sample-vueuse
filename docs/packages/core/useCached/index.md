[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useCached/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowOrDeepRef` | `@vueuse/shared` |
| `Ref` | `vue` |
| `WatchOptions` | `vue` |
| `ConfigurableDeepRefs` | `../_configurable` |
| `createRef` | `@vueuse/shared` |
| `watch` | `vue` |


---

## Functions

### `useCached(refValue: Ref<T>, comparator: (a: T, b: T) => boolean, options: UseCachedOptions<D>): UseCachedReturn<T, D>`

<details><summary>Code</summary>

```ts
export function useCached<T, D extends boolean = true>(
  refValue: Ref<T>,
  comparator: (a: T, b: T) => boolean = (a, b) => a === b,
  options?: UseCachedOptions<D>,
): UseCachedReturn<T, D> {
  const { deepRefs = true as D, ...watchOptions } = options || {}
  const cachedValue = createRef(refValue.value, deepRefs)

  watch(() => refValue.value, (value) => {
    if (!comparator(value, cachedValue.value))
      cachedValue.value = value
  }, watchOptions)

  return cachedValue
}
```
</details>

- **Parameters**:
  - `refValue: Ref<T>`
  - `comparator: (a: T, b: T) => boolean`
  - `options: UseCachedOptions<D>`
- **Return Type**: `UseCachedReturn<T, D>`
- **Calls**:
  - `createRef (from @vueuse/shared)`
  - `watch (from vue)`
  - `comparator`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseCachedOptions<D extends boolean = true>`

<details><summary>Interface Code</summary>

```ts
export interface UseCachedOptions<D extends boolean = true> extends ConfigurableDeepRefs<D>, WatchOptions {}
```
</details>


---

## Type Aliases

### `UseCachedReturn<T = any = any, D extends boolean = true extends boolean = true>`

```ts
type UseCachedReturn<T = any = any, D extends boolean = true extends boolean = true> = ShallowOrDeepRef<T, D>;
```


---