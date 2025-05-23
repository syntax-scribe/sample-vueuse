[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useWebWorkerFn/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useDateFormat` | `@vueuse/core` |
| `useTimestamp` | `@vueuse/core` |
| `useWebWorkerFn` | `@vueuse/core` |
| `computed` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `heavyTask(): number[]`

<details><summary>Code</summary>

```ts
function heavyTask() {
  const randomNumber = () => Math.trunc(Math.random() * 5_000_00)
  const numbers: number[] = Array.from({ length: 5_000_000 }).fill(undefined).map(randomNumber)
  numbers.sort()
  return numbers.slice(0, 5)
}
```
</details>

- **Return Type**: `number[]`
- **Calls**:
  - `Math.trunc`
  - `Math.random`
  - `Array.from({ length: 5_000_000 }).fill(undefined).map`
  - `numbers.sort`
  - `numbers.slice`
### `randomNumber(): number`

<details><summary>Code</summary>

```ts
() => Math.trunc(Math.random() * 5_000_00)
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `Math.trunc`
### `baseSort(): Promise<void>`

<details><summary>Code</summary>

```ts
async function baseSort() {
  data.value = null
  await nextTick()
  data.value = heavyTask()
  runner.value = 'Main'
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `nextTick (from vue)`
  - `heavyTask`
### `workerSort(): Promise<void>`

<details><summary>Code</summary>

```ts
async function workerSort() {
  data.value = null
  await nextTick()
  data.value = await workerFn()
  runner.value = 'Worker'
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `nextTick (from vue)`
  - `workerFn`

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