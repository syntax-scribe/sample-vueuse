[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/useToggle/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `isRef` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `_value` | `ShallowRef<boolean>` | const | `shallowRef(initialValue) as ShallowRef<boolean>` | ✗ |


---

## Functions

### `useToggle(initialValue: Ref<T>, options: UseToggleOptions<Truthy, Falsy>): (value?: T) => T`

<details><summary>Code</summary>

```ts
export function useToggle<Truthy, Falsy, T = Truthy | Falsy>(initialValue: Ref<T>, options?: UseToggleOptions<Truthy, Falsy>): (value?: T) => T
```
</details>

- **Parameters**:
  - `initialValue: Ref<T>`
  - `options: UseToggleOptions<Truthy, Falsy>`
- **Return Type**: `(value?: T) => T`
### `toggle(value: boolean): any`

<details><summary>Code</summary>

```ts
function toggle(value?: boolean) {
    // has arguments
    if (arguments.length) {
      _value.value = value!
      return _value.value
    }
    else {
      const truthy = toValue(truthyValue)
      _value.value = _value.value === truthy
        ? toValue(falsyValue)
        : truthy
      return _value.value
    }
  }
```
</details>

- **Parameters**:
  - `value: boolean`
- **Return Type**: `any`
- **Calls**:
  - `toValue (from vue)`
- **Internal Comments**:
```
// has arguments
```


---

## Interfaces

### `UseToggleOptions<Truthy, Falsy>`

<details><summary>Interface Code</summary>

```ts
export interface UseToggleOptions<Truthy, Falsy> {
  truthyValue?: MaybeRefOrGetter<Truthy>
  falsyValue?: MaybeRefOrGetter<Falsy>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `truthyValue` | `MaybeRefOrGetter<Truthy>` | ✓ |  |
| `falsyValue` | `MaybeRefOrGetter<Falsy>` | ✓ |  |


---

## Type Aliases

### `ToggleFn`

```ts
type ToggleFn = (value?: boolean) => void;
```

### `UseToggleReturn`

```ts
type UseToggleReturn = [ShallowRef<boolean>, ToggleFn] | ToggleFn;
```


---