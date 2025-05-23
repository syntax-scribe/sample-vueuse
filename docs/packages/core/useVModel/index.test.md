[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Classes](#classes)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 1
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useVModel/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `nextTick` | `vue` |
| `useVModel` | `./index` |


---

## Functions

### `defaultProps(): { modelValue: string; }`

<details><summary>Code</summary>

```ts
() => ({
    [defaultKey]: defaultValue,
  })
```
</details>

- **Return Type**: `{ modelValue: string; }`
### `SomeClass.someMethod(): void`

<details><summary>Code</summary>

```ts
someMethod() {}
```
</details>

- **Return Type**: `void`
### `beforeEmit(value: string): boolean`

<details><summary>Code</summary>

```ts
(value: string) => {
      res = value
      beforeEmitMock()
      return true
    }
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `boolean`
- **Calls**:
  - `beforeEmitMock`
### `beforeEmit(value: string): boolean`

<details><summary>Code</summary>

```ts
(value: string) => {
      res = value
      beforeEmitMock()
      return false
    }
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `boolean`
- **Calls**:
  - `beforeEmitMock`

---

## Classes

### `SomeClass`

<details><summary>Class Code</summary>

```ts
class SomeClass {
      num1 = 1

      someMethod() {}
    }
```
</details>

#### Methods

##### `someMethod(): void`

<details><summary>Code</summary>

```ts
someMethod() {}
```
</details>


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---