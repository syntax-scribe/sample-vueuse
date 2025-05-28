[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/reactify/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `AnyFn` | `../utils` |
| `computed` | `vue` |
| `toValue` | `vue` |
| `unref` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `unrefFn` | `any` | const | `options?.computedGetter === false ? unref : toValue` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `reactify(fn: T, options: ReactifyOptions<K>): ReactifyReturn<T, K>`

<details><summary>Code</summary>

```ts
export function reactify<T extends AnyFn, K extends boolean = true>(fn: T, options?: ReactifyOptions<K>): ReactifyReturn<T, K> {
  const unrefFn = options?.computedGetter === false ? unref : toValue
  return function (this: any, ...args: any[]) {
    return computed(() => fn.apply(this, args.map(i => unrefFn(i))))
  } as any
}
```
</details>

- **JSDoc**:
```ts
/**
 * Converts plain function into a reactive function.
 * The converted function accepts refs as it's arguments
 * and returns a ComputedRef, with proper typing.
 *
 * @param fn - Source function
 * @param options - Options
 */
```

- **Parameters**:
  - `fn: T`
  - `options: ReactifyOptions<K>`
- **Return Type**: `ReactifyReturn<T, K>`
- **Calls**:
  - `computed (from vue)`
  - `fn.apply`
  - `args.map`
  - `unrefFn`

---

## Interfaces

### `ReactifyOptions<T extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface ReactifyOptions<T extends boolean> {
  /**
   * Accept passing a function as a reactive getter
   *
   * @default true
   */
  computedGetter?: T
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `computedGetter` | `T` | ✓ |  |


---

## Type Aliases

### `Reactified<T, Computed extends boolean extends boolean>`

```ts
type Reactified<T, Computed extends boolean extends boolean> = T extends (...args: infer A) => infer R
  ? (...args: { [K in keyof A]: Computed extends true ? MaybeRefOrGetter<A[K]> : MaybeRef<A[K]> }) => ComputedRef<R>
  : never;
```

### `ReactifyReturn<T extends AnyFn = AnyFn extends AnyFn = AnyFn, K extends boolean = true extends boolean = true>`

```ts
type ReactifyReturn<T extends AnyFn = AnyFn extends AnyFn = AnyFn, K extends boolean = true extends boolean = true> = Reactified<T, K>;
```


---