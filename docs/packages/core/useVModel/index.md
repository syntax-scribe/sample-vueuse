[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useVModel/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `UnwrapRef` | `vue` |
| `WritableComputedRef` | `vue` |
| `CloneFn` | `../useCloned` |
| `isDef` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `getCurrentInstance` | `vue` |
| `nextTick` | `vue` |
| `watch` | `vue` |
| `cloneFnJSON` | `../useCloned` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `_emit` | `any` | const | `emit || vm?.emit || vm?.$emit?.bind(vm) || vm?.proxy?.$emit?.bind(vm?.proxy)` | ✗ |
| `event` | `string | undefined` | let/var | `eventName` | ✗ |
| `isUpdating` | `boolean` | let/var | `false` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `computed` | computed | *none* | *none* |


---

## Functions

### `useVModel(props: P, key: K, emit: (name: Name, ...args: any[]) => void, options: UseVModelOptions<P[K], false>): WritableComputedRef<P[K]>`

<details><summary>Code</summary>

```ts
export function useVModel<P extends object, K extends keyof P, Name extends string>(
  props: P,
  key?: K,
  emit?: (name: Name, ...args: any[]) => void,
  options?: UseVModelOptions<P[K], false>,
): WritableComputedRef<P[K]>
```
</details>

- **Parameters**:
  - `props: P`
  - `key: K`
  - `emit: (name: Name, ...args: any[]) => void`
  - `options: UseVModelOptions<P[K], false>`
- **Return Type**: `WritableComputedRef<P[K]>`
### `cloneFn(val: P[K]): P[K]`

<details><summary>Code</summary>

```ts
(val: P[K]) => !clone
    ? val
    : typeof clone === 'function'
      ? clone(val)
      : cloneFnJSON(val)
```
</details>

- **Parameters**:
  - `val: P[K]`
- **Return Type**: `P[K]`
### `getValue(): P[K]`

<details><summary>Code</summary>

```ts
() => isDef(props[key!])
    ? cloneFn(props[key!])
    : defaultValue
```
</details>

- **Return Type**: `P[K]`
### `triggerEmit(value: P[K]): void`

<details><summary>Code</summary>

```ts
(value: P[K]) => {
    if (shouldEmit) {
      if (shouldEmit(value))
        _emit(event, value)
    }
    else {
      _emit(event, value)
    }
  }
```
</details>

- **Parameters**:
  - `value: P[K]`
- **Return Type**: `void`
- **Calls**:
  - `shouldEmit`
  - `_emit`

---

## Interfaces

### `UseVModelOptions<T, Passive extends boolean = false>`

<details><summary>Interface Code</summary>

```ts
export interface UseVModelOptions<T, Passive extends boolean = false> {
  /**
   * When passive is set to `true`, it will use `watch` to sync with props and ref.
   * Instead of relying on the `v-model` or `.sync` to work.
   *
   * @default false
   */
  passive?: Passive
  /**
   * When eventName is set, it's value will be used to overwrite the emit event name.
   *
   * @default undefined
   */
  eventName?: string
  /**
   * Attempting to check for changes of properties in a deeply nested object or array.
   * Apply only when `passive` option is set to `true`
   *
   * @default false
   */
  deep?: boolean
  /**
   * Defining default value for return ref when no value is passed.
   *
   * @default undefined
   */
  defaultValue?: T
  /**
   * Clone the props.
   * Accepts a custom clone function.
   * When setting to `true`, it will use `JSON.parse(JSON.stringify(value))` to clone.
   *
   * @default false
   */
  clone?: boolean | CloneFn<T>
  /**
   * The hook before triggering the emit event can be used for form validation.
   * if false is returned, the emit event will not be triggered.
   *
   * @default undefined
   */
  shouldEmit?: (v: T) => boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `passive` | `Passive` | ✓ |  |
| `eventName` | `string` | ✓ |  |
| `deep` | `boolean` | ✓ |  |
| `defaultValue` | `T` | ✓ |  |
| `clone` | `boolean | CloneFn<T>` | ✓ |  |
| `shouldEmit` | `(v: T) => boolean` | ✓ |  |


---