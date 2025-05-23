[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useArrayUnique/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `uniq(array: T[]): T[]`

<details><summary>Code</summary>

```ts
function uniq<T>(array: T[]) {
  return Array.from(new Set(array))
}
```
</details>

- **Parameters**:
  - `array: T[]`
- **Return Type**: `T[]`
- **Calls**:
  - `Array.from`
### `uniqueElementsBy(array: T[], fn: (a: T, b: T, array: T[]) => boolean): T[]`

<details><summary>Code</summary>

```ts
function uniqueElementsBy<T>(
  array: T[],
  fn: (a: T, b: T, array: T[]) => boolean,
) {
  return array.reduce<T[]>((acc, v) => {
    if (!acc.some(x => fn(v, x, array)))
      acc.push(v)
    return acc
  }, [])
}
```
</details>

- **Parameters**:
  - `array: T[]`
  - `fn: (a: T, b: T, array: T[]) => boolean`
- **Return Type**: `T[]`
- **Calls**:
  - `array.reduce`
  - `acc.some`
  - `fn`
  - `acc.push`
### `useArrayUnique(list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>, compareFn: (a: T, b: T, array: T[]) => boolean): UseArrayUniqueReturn<T>`

<details><summary>Code</summary>

```ts
export function useArrayUnique<T>(
  list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>,
  compareFn?: (a: T, b: T, array: T[]) => boolean,
): UseArrayUniqueReturn<T> {
  return computed<T[]>(() => {
    const resolvedList = toValue(list).map(element => toValue(element))
    return compareFn ? uniqueElementsBy(resolvedList, compareFn) : uniq(resolvedList)
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * reactive unique array
 * @see https://vueuse.org/useArrayUnique
 * @param list - the array was called upon.
 * @param compareFn
 * @returns A computed ref that returns a unique array of items.
 */
```

- **Parameters**:
  - `list: MaybeRefOrGetter<MaybeRefOrGetter<T>[]>`
  - `compareFn: (a: T, b: T, array: T[]) => boolean`
- **Return Type**: `UseArrayUniqueReturn<T>`
- **Calls**:
  - `computed (from vue)`
  - `toValue(list).map`
  - `toValue (from vue)`
  - `uniqueElementsBy`
  - `uniq`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseArrayUniqueReturn<T = any = any>`

```ts
type UseArrayUniqueReturn<T = any = any> = ComputedRef<T[]>;
```


---