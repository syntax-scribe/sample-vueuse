[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useObjectUrl/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `readonly` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useObjectUrl(object: MaybeRefOrGetter<Blob | MediaSource | null | undefined>): any`

<details><summary>Code</summary>

```ts
export function useObjectUrl(object: MaybeRefOrGetter<Blob | MediaSource | null | undefined>) {
  const url = shallowRef<string | undefined>()

  const release = () => {
    if (url.value)
      URL.revokeObjectURL(url.value)

    url.value = undefined
  }

  watch(
    () => toValue(object),
    (newObject) => {
      release()

      if (newObject)
        url.value = URL.createObjectURL(newObject)
    },
    { immediate: true },
  )

  tryOnScopeDispose(release)

  return readonly(url)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive URL representing an object.
 *
 * @see https://vueuse.org/useObjectUrl
 * @param object
 */
```

- **Parameters**:
  - `object: MaybeRefOrGetter<Blob | MediaSource | null | undefined>`
- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `URL.revokeObjectURL`
  - `watch (from vue)`
  - `toValue (from vue)`
  - `release`
  - `URL.createObjectURL`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `readonly (from vue)`
### `release(): void`

<details><summary>Code</summary>

```ts
() => {
    if (url.value)
      URL.revokeObjectURL(url.value)

    url.value = undefined
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `URL.revokeObjectURL`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---