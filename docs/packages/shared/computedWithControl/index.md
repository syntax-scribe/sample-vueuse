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
- **Interfaces**: 3
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/shared/computedWithControl/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedGetter` | `vue` |
| `ComputedRef` | `vue` |
| `WatchSource` | `vue` |
| `WritableComputedOptions` | `vue` |
| `WritableComputedRef` | `vue` |
| `Fn` | `../utils` |
| `customRef` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |


---

## Functions

### `computedWithControl(source: WatchSource<S> | WatchSource<S>[], fn: ComputedGetter<T>): ComputedRefWithControl<T>`

<details><summary>Code</summary>

```ts
export function computedWithControl<T, S>(
  source: WatchSource<S> | WatchSource<S>[],
  fn: ComputedGetter<T>
): ComputedRefWithControl<T>
```
</details>

- **Parameters**:
  - `source: WatchSource<S> | WatchSource<S>[]`
  - `fn: ComputedGetter<T>`
- **Return Type**: `ComputedRefWithControl<T>`
### `update(): void`

<details><summary>Code</summary>

```ts
() => {
    dirty.value = true
    trigger()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `trigger`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `ComputedWithControlRefExtra`

<details><summary>Interface Code</summary>

```ts
export interface ComputedWithControlRefExtra {
  /**
   * Force update the computed value.
   */
  trigger: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `trigger` | `() => void` | ✗ |  |

### `ComputedRefWithControl<T>`

<details><summary>Interface Code</summary>

```ts
export interface ComputedRefWithControl<T> extends ComputedRef<T>, ComputedWithControlRefExtra {}
```
</details>

### `WritableComputedRefWithControl<T>`

<details><summary>Interface Code</summary>

```ts
export interface WritableComputedRefWithControl<T> extends WritableComputedRef<T>, ComputedWithControlRefExtra {}
```
</details>


---

## Type Aliases

### `ComputedWithControlRef<T = any = any>`

```ts
type ComputedWithControlRef<T = any = any> = ComputedRefWithControl<T> | WritableComputedRefWithControl<T>;
```


---