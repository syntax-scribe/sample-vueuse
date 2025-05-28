[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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