[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


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

## Type Aliases

### `UseArrayJoinReturn`

```ts
type UseArrayJoinReturn = ComputedRef<string>;
```


---