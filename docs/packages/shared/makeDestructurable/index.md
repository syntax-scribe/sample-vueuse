[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 5
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/makeDestructurable/index.ts`**

## 📦 Imports

> No imports found in this file.


---

## Functions

### `makeDestructurable(obj: T, arr: A): T & A`

<details><summary>Code</summary>

```ts
export function makeDestructurable<
  T extends Record<string, unknown>,
  A extends readonly any[],
>(obj: T, arr: A): T & A {
  if (typeof Symbol !== 'undefined') {
    const clone = { ...obj }

    Object.defineProperty(clone, Symbol.iterator, {
      enumerable: false,
      value() {
        let index = 0
        return {
          next: () => ({
            value: arr[index++],
            done: index > arr.length,
          }),
        }
      },
    })

    return clone as T & A
  }
  else {
    return Object.assign([...arr], obj) as unknown as T & A
  }
}
```
</details>

- **Parameters**:
  - `obj: T`
  - `arr: A`
- **Return Type**: `T & A`
- **Calls**:
  - `Object.defineProperty`
  - `Object.assign`
### `next(): { value: any; done: boolean; }`

<details><summary>Code</summary>

```ts
() => ({
            value: arr[index++],
            done: index > arr.length,
          })
```
</details>

- **Return Type**: `{ value: any; done: boolean; }`
### `next(): { value: any; done: boolean; }`

<details><summary>Code</summary>

```ts
() => ({
            value: arr[index++],
            done: index > arr.length,
          })
```
</details>

- **Return Type**: `{ value: any; done: boolean; }`
### `next(): { value: any; done: boolean; }`

<details><summary>Code</summary>

```ts
() => ({
            value: arr[index++],
            done: index > arr.length,
          })
```
</details>

- **Return Type**: `{ value: any; done: boolean; }`
### `next(): { value: any; done: boolean; }`

<details><summary>Code</summary>

```ts
() => ({
            value: arr[index++],
            done: index > arr.length,
          })
```
</details>

- **Return Type**: `{ value: any; done: boolean; }`

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