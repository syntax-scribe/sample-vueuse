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
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/extendRef/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ShallowUnwrapRef` | `vue` |
| `UnwrapRef` | `vue` |
| `isRef` | `vue` |


---

## Functions

### `extendRef(ref: R, extend: Extend, options: Options): ShallowUnwrapRef<Extend> & R`

<details><summary>Code</summary>

```ts
export function extendRef<R extends Ref<any>, Extend extends object, Options extends ExtendRefOptions<false>>(ref: R, extend: Extend, options?: Options): ShallowUnwrapRef<Extend> & R
```
</details>

- **JSDoc**:
```ts
/**
 * Overload 1: Unwrap set to false
 */
```

- **Parameters**:
  - `ref: R`
  - `extend: Extend`
  - `options: Options`
- **Return Type**: `ShallowUnwrapRef<Extend> & R`

---

## Interfaces

### `ExtendRefOptions<Unwrap extends boolean = boolean>`

<details><summary>Interface Code</summary>

```ts
export interface ExtendRefOptions<Unwrap extends boolean = boolean> {
  /**
   * Is the extends properties enumerable
   *
   * @default false
   */
  enumerable?: boolean

  /**
   * Unwrap for Ref properties
   *
   * @default true
   */
  unwrap?: Unwrap
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `enumerable` | `boolean` | ✓ |  |
| `unwrap` | `Unwrap` | ✓ |  |


---

## Type Aliases

### `ExtendRefReturn<T = any = any>`

```ts
type ExtendRefReturn<T = any = any> = Ref<T>;
```


---