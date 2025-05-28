[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 6 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 3 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `v` | `T` | let/var | `undefined!` | ✗ |
| `track` | `Fn` | let/var | `*not shown*` | ✗ |
| `trigger` | `Fn` | let/var | `*not shown*` | ✗ |
| `get` | `any` | const | `typeof fn === 'function' ? fn : fn.get` | ✗ |
| `set` | `any` | const | `typeof fn === 'function' ? undefined : fn.set` | ✗ |
| `result` | `ComputedRefWithControl<T>` | const | `customRef<T>((_track, _trigger) => {
    track = _track
    trigger = _trigger

    return {
      get() {
        if (dirty.value) {
          v = get(v)
          dirty.value = false
        }
        track()
        return v
      },
      set(v) {
        set?.(v)
      },
    }
  }) as ComputedRefWithControl<T>` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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