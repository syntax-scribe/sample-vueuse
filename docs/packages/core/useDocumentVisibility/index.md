[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useDocumentVisibility/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useDocumentVisibility(options: ConfigurableDocument): ShallowRef<DocumentVisibilityState>`

<details><summary>Code</summary>

```ts
export function useDocumentVisibility(options: ConfigurableDocument = {}): ShallowRef<DocumentVisibilityState> {
  const { document = defaultDocument } = options
  if (!document)
    return shallowRef('visible')

  const visibility = shallowRef(document.visibilityState)

  useEventListener(document, 'visibilitychange', () => {
    visibility.value = document.visibilityState
  }, { passive: true })

  return visibility
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively track `document.visibilityState`.
 *
 * @see https://vueuse.org/useDocumentVisibility
 */
```

- **Parameters**:
  - `options: ConfigurableDocument`
- **Return Type**: `ShallowRef<DocumentVisibilityState>`
- **Calls**:
  - `shallowRef (from vue)`
  - `useEventListener (from ../useEventListener)`

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