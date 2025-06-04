[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

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