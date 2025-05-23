[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 1
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/integrations/useFuse/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `FuseResult` | `fuse.js` |
| `IFuseOptions` | `fuse.js` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Fuse` | `fuse.js` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useFuse(search: MaybeRefOrGetter<string>, data: MaybeRefOrGetter<DataItem[]>, options: MaybeRefOrGetter<UseFuseOptions<DataItem>>): { fuse: any; results: ComputedRef<FuseResult<DataItem>[]>; }`

<details><summary>Code</summary>

```ts
export function useFuse<DataItem>(
  search: MaybeRefOrGetter<string>,
  data: MaybeRefOrGetter<DataItem[]>,
  options?: MaybeRefOrGetter<UseFuseOptions<DataItem>>,
) {
  const createFuse = () => {
    return new Fuse(
      toValue(data) ?? [],
      toValue(options)?.fuseOptions,
    )
  }

  const fuse = deepRef(createFuse())

  watch(
    () => toValue(options)?.fuseOptions,
    () => { fuse.value = createFuse() },
    { deep: true },
  )

  watch(
    () => toValue(data),
    (newData) => { fuse.value.setCollection(newData) },
    { deep: true },
  )

  const results: ComputedRef<FuseResult<DataItem>[]> = computed(() => {
    const resolved = toValue(options)
    // This will also be recomputed when `data` changes, as it causes a change
    // to the Fuse instance, which is tracked here.
    if (resolved?.matchAllWhenSearchEmpty && !toValue(search))
      return toValue(data).map((item, index) => ({ item, refIndex: index }))

    const limit = resolved?.resultLimit
    return fuse.value.search(toValue(search), (limit ? { limit } : undefined))
  })

  return {
    fuse,
    results,
  }
}
```
</details>

- **Parameters**:
  - `search: MaybeRefOrGetter<string>`
  - `data: MaybeRefOrGetter<DataItem[]>`
  - `options: MaybeRefOrGetter<UseFuseOptions<DataItem>>`
- **Return Type**: `{ fuse: any; results: ComputedRef<FuseResult<DataItem>[]>; }`
- **Calls**:
  - `toValue (from vue)`
  - `deepRef (from vue)`
  - `createFuse`
  - `watch (from vue)`
  - `fuse.value.setCollection`
  - `computed (from vue)`
  - `toValue(data).map`
  - `fuse.value.search`
- **Internal Comments**:
```
// This will also be recomputed when `data` changes, as it causes a change
// to the Fuse instance, which is tracked here.
```

### `createFuse(): any`

<details><summary>Code</summary>

```ts
() => {
    return new Fuse(
      toValue(data) ?? [],
      toValue(options)?.fuseOptions,
    )
  }
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `toValue (from vue)`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseFuseOptions<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseFuseOptions<T> {
  fuseOptions?: FuseOptions<T>
  resultLimit?: number
  matchAllWhenSearchEmpty?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `fuseOptions` | `FuseOptions<T>` | ✓ |  |
| `resultLimit` | `number` | ✓ |  |
| `matchAllWhenSearchEmpty` | `boolean` | ✓ |  |


---

## Type Aliases

### `FuseOptions<T>`

```ts
type FuseOptions<T> = IFuseOptions<T>;
```

### `UseFuseReturn`

```ts
type UseFuseReturn = ReturnType<typeof useFuse>;
```


---