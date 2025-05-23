[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useArrayJoin/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `useArrayJoin(list: MaybeRefOrGetter<MaybeRefOrGetter<any>[]>, separator: MaybeRefOrGetter<string>): UseArrayJoinReturn`

<details><summary>Code</summary>

```ts
export function useArrayJoin(
  list: MaybeRefOrGetter<MaybeRefOrGetter<any>[]>,
  separator?: MaybeRefOrGetter<string>,
): UseArrayJoinReturn {
  return computed(() => toValue(list).map(i => toValue(i)).join(toValue(separator)))
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `Array.join`
 *
 * @see https://vueuse.org/useArrayJoin
 * @param list - the array was called upon.
 * @param separator - a string to separate each pair of adjacent elements of the array. If omitted, the array elements are separated with a comma (",").
 *
 * @returns a string with all array elements joined. If arr.length is 0, the empty string is returned.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<any>[]>`
  - `separator: MaybeRefOrGetter<string>`
- **Return Type**: `UseArrayJoinReturn`
- **Calls**:
  - `computed (from vue)`
  - `toValue(list).map(i => toValue(i)).join`
  - `toValue (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseArrayJoinReturn`

```ts
type UseArrayJoinReturn = ComputedRef<string>;
```


---