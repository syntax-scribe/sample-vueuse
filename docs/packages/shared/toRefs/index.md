[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 4 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/toRefs/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ToRefs` | `vue` |
| `_toRefs` | `vue` |
| `customRef` | `vue` |
| `isRef` | `vue` |
| `toValue` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `result` | `any` | const | `Array.isArray(objectRef.value)
    ? Array.from({ length: objectRef.value.length })
    : {}` | ✗ |
| `replaceRef` | `any` | const | `toValue(options.replaceRef) ?? true` | ✗ |
| `copy` | `any` | const | `[...objectRef.value]` | ✗ |
| `newObject` | `any` | const | `{ ...objectRef.value, [key]: v }` | ✗ |


---

## Functions

### `toRefs(objectRef: MaybeRef<T>, options: ToRefsOptions): ToRefs<T>`

<details><summary>Code</summary>

```ts
export function toRefs<T extends object>(
  objectRef: MaybeRef<T>,
  options: ToRefsOptions = {},
): ToRefs<T> {
  if (!isRef(objectRef))
    return _toRefs(objectRef)

  const result: any = Array.isArray(objectRef.value)
    ? Array.from({ length: objectRef.value.length })
    : {}

  for (const key in objectRef.value) {
    result[key] = customRef<T[typeof key]>(() => ({
      get() {
        return objectRef.value[key]
      },
      set(v) {
        const replaceRef = toValue(options.replaceRef) ?? true

        if (replaceRef) {
          if (Array.isArray(objectRef.value)) {
            const copy: any = [...objectRef.value]
            copy[key] = v
            objectRef.value = copy
          }
          else {
            const newObject = { ...objectRef.value, [key]: v }

            Object.setPrototypeOf(newObject, Object.getPrototypeOf(objectRef.value))

            objectRef.value = newObject
          }
        }
        else {
          objectRef.value[key] = v
        }
      },
    }))
  }
  return result
}
```
</details>

- **JSDoc**:
```ts
/**
 * Extended `toRefs` that also accepts refs of an object.
 *
 * @see https://vueuse.org/toRefs
 * @param objectRef A ref or normal object or array.
 * @param options Options
 */
```

- **Parameters**:
  - `objectRef: MaybeRef<T>`
  - `options: ToRefsOptions`
- **Return Type**: `ToRefs<T>`
- **Calls**:
  - `isRef (from vue)`
  - `_toRefs (from vue)`
  - `Array.isArray`
  - `Array.from`
  - `customRef (from vue)`
  - `toValue (from vue)`
  - `Object.setPrototypeOf`
  - `Object.getPrototypeOf`

---

## Interfaces

### `ToRefsOptions`

<details><summary>Interface Code</summary>

```ts
export interface ToRefsOptions {
  /**
   * Replace the original ref with a copy on property update.
   *
   * @default true
   */
  replaceRef?: MaybeRefOrGetter<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `replaceRef` | `MaybeRefOrGetter<boolean>` | ✓ |  |


---