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
📂 **`packages/shared/toReactive/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `UnwrapNestedRefs` | `vue` |
| `isRef` | `vue` |
| `reactive` | `vue` |
| `unref` | `vue` |


---

## Functions

### `toReactive(objectRef: MaybeRef<T>): UnwrapNestedRefs<T>`

<details><summary>Code</summary>

```ts
export function toReactive<T extends object>(
  objectRef: MaybeRef<T>,
): UnwrapNestedRefs<T> {
  if (!isRef(objectRef))
    return reactive(objectRef)

  const proxy = new Proxy({}, {
    get(_, p, receiver) {
      return unref(Reflect.get(objectRef.value, p, receiver))
    },
    set(_, p, value) {
      if (isRef((objectRef.value as any)[p]) && !isRef(value))
        (objectRef.value as any)[p].value = value
      else
        (objectRef.value as any)[p] = value
      return true
    },
    deleteProperty(_, p) {
      return Reflect.deleteProperty(objectRef.value, p)
    },
    has(_, p) {
      return Reflect.has(objectRef.value, p)
    },
    ownKeys() {
      return Object.keys(objectRef.value)
    },
    getOwnPropertyDescriptor() {
      return {
        enumerable: true,
        configurable: true,
      }
    },
  })

  return reactive(proxy) as UnwrapNestedRefs<T>
}
```
</details>

- **JSDoc**:
```ts
/**
 * Converts ref to reactive.
 *
 * @see https://vueuse.org/toReactive
 * @param objectRef A ref of object
 */
```

- **Parameters**:
  - `objectRef: MaybeRef<T>`
- **Return Type**: `UnwrapNestedRefs<T>`
- **Calls**:
  - `isRef (from vue)`
  - `reactive (from vue)`
  - `unref (from vue)`
  - `Reflect.get`
  - `Reflect.deleteProperty`
  - `Reflect.has`
  - `Object.keys`

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