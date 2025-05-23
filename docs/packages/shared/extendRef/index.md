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
- **Imports**: 4
- **Interfaces**: 1
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


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