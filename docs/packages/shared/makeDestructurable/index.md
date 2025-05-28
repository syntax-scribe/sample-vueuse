[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 🧱 Classes | 0 |
| 📦 Imports | 0 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/makeDestructurable/index.ts`**

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `clone` | `T` | const | `{ ...obj }` | ✗ |
| `index` | `number` | let/var | `0` | ✗ |


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