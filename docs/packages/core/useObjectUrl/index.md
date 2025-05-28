[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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