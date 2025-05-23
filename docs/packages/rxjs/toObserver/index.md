[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/rxjs/toObserver/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `NextObserver` | `rxjs` |
| `Ref` | `vue` |


---

## Functions

### `toObserver(value: Ref<T>): NextObserver<T>`

<details><summary>Code</summary>

```ts
export function toObserver<T>(value: Ref<T>): NextObserver<T> {
  return {
    next: (val: T) => {
      value.value = val
    },
  }
}
```
</details>

- **Parameters**:
  - `value: Ref<T>`
- **Return Type**: `NextObserver<T>`
### `next(val: T): void`

<details><summary>Code</summary>

```ts
(val: T) => {
      value.value = val
    }
```
</details>

- **Parameters**:
  - `val: T`
- **Return Type**: `void`
### `next(val: T): void`

<details><summary>Code</summary>

```ts
(val: T) => {
      value.value = val
    }
```
</details>

- **Parameters**:
  - `val: T`
- **Return Type**: `void`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---