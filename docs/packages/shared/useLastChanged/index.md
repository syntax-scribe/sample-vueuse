[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/useLastChanged/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ShallowRef` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `shallowReadonly` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |
| `timestamp` | `../utils` |


---

## Functions

### `useLastChanged(source: WatchSource, options: UseLastChangedOptions<false>): Readonly<ShallowRef<number | null>>`

<details><summary>Code</summary>

```ts
export function useLastChanged(source: WatchSource, options?: UseLastChangedOptions<false>): Readonly<ShallowRef<number | null>>
```
</details>

- **JSDoc**:
```ts
/**
 * Records the timestamp of the last change
 *
 * @see https://vueuse.org/useLastChanged
 */
```

- **Parameters**:
  - `source: WatchSource`
  - `options: UseLastChangedOptions<false>`
- **Return Type**: `Readonly<ShallowRef<number | null>>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseLastChangedOptions<Immediate extends boolean, InitialValue extends number | null | undefined = undefined>`

<details><summary>Interface Code</summary>

```ts
export interface UseLastChangedOptions<
  Immediate extends boolean,
  InitialValue extends number | null | undefined = undefined,
> extends WatchOptions<Immediate> {
  initialValue?: InitialValue
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialValue` | `InitialValue` | ✓ |  |


---

## Type Aliases

### `UseLastChangedReturn`

```ts
type UseLastChangedReturn = Readonly<ShallowRef<number | null>> | Readonly<ShallowRef<number>>;
```


---