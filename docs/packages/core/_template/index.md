[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 📦 Imports | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/_template/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `shallowRef` | `vue` |


---

## Functions

### `useCounter(initialValue: number): { count: any; inc: (delta?: number) => any; dec: (delta?: number) => number; get: () => any; set: (val: number) => number; reset: (val?: number) => number; }`

<details><summary>Code</summary>

```ts
export function useCounter(initialValue = 0) {
  const count = shallowRef(initialValue)

  const inc = (delta = 1) => (count.value += delta)
  const dec = (delta = 1) => (count.value -= delta)
  const get = () => count.value
  const set = (val: number) => (count.value = val)
  const reset = (val = initialValue) => {
    initialValue = val
    return set(val)
  }

  return { count, inc, dec, get, set, reset }
}
```
</details>

- **Parameters**:
  - `initialValue: number`
- **Return Type**: `{ count: any; inc: (delta?: number) => any; dec: (delta?: number) => number; get: () => any; set: (val: number) => number; reset: (val?: number) => number; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `set`
### `inc(delta: number): any`

<details><summary>Code</summary>

```ts
(delta = 1) => (count.value += delta)
```
</details>

- **Parameters**:
  - `delta: number`
- **Return Type**: `any`
### `dec(delta: number): number`

<details><summary>Code</summary>

```ts
(delta = 1) => (count.value -= delta)
```
</details>

- **Parameters**:
  - `delta: number`
- **Return Type**: `number`
### `get(): any`

<details><summary>Code</summary>

```ts
() => count.value
```
</details>

- **Return Type**: `any`
### `set(val: number): number`

<details><summary>Code</summary>

```ts
(val: number) => (count.value = val)
```
</details>

- **Parameters**:
  - `val: number`
- **Return Type**: `number`
### `reset(val: number): number`

<details><summary>Code</summary>

```ts
(val = initialValue) => {
    initialValue = val
    return set(val)
  }
```
</details>

- **Parameters**:
  - `val: number`
- **Return Type**: `number`
- **Calls**:
  - `set`

---