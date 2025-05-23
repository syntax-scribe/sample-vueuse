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
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/shared/reactifyObject/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Reactified` | `../reactify` |
| `ReactifyOptions` | `../reactify` |
| `AnyFn` | `../utils` |
| `reactify` | `../reactify` |


---

## Functions

### `reactifyObject(obj: T, keys: (keyof T)[]): ReactifyObjectReturn<T, Keys, true>`

<details><summary>Code</summary>

```ts
export function reactifyObject<T extends object, Keys extends keyof T>(obj: T, keys?: (keyof T)[]): ReactifyObjectReturn<T, Keys, true>
```
</details>

- **JSDoc**:
```ts
/**
 * Apply `reactify` to an object
 */
```

- **Parameters**:
  - `obj: T`
  - `keys: (keyof T)[]`
- **Return Type**: `ReactifyObjectReturn<T, Keys, true>`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `ReactifyObjectOptions<T extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface ReactifyObjectOptions<T extends boolean> extends ReactifyOptions<T> {
  /**
   * Includes names from Object.getOwnPropertyNames
   *
   * @default true
   */
  includeOwnProperties?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `includeOwnProperties` | `boolean` | ✓ |  |


---

## Type Aliases

### `ReactifyNested<T, Keys extends keyof T = keyof T extends keyof T = keyof T, S extends boolean = true extends boolean = true>`

```ts
type ReactifyNested<T, Keys extends keyof T = keyof T extends keyof T = keyof T, S extends boolean = true extends boolean = true> = { [K in Keys]: T[K] extends AnyFn ? Reactified<T[K], S> : T[K] };
```

### `ReactifyObjectReturn<T, Keys extends keyof T extends keyof T, S extends boolean = true extends boolean = true>`

```ts
type ReactifyObjectReturn<T, Keys extends keyof T extends keyof T, S extends boolean = true extends boolean = true> = ReactifyNested<T, Keys, S>;
```


---