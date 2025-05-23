[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useMounted/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `getCurrentInstance` | `vue` |
| `onMounted` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `useMounted(): any`

<details><summary>Code</summary>

```ts
export function useMounted() {
  const isMounted = shallowRef(false)

  const instance = getCurrentInstance()
  if (instance) {
    onMounted(() => {
      isMounted.value = true
    }, instance)
  }

  return isMounted
}
```
</details>

- **JSDoc**:
```ts
/**
 * Mounted state in ref.
 *
 * @see https://vueuse.org/useMounted
 */
```

- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `getCurrentInstance (from vue)`
  - `onMounted (from vue)`

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