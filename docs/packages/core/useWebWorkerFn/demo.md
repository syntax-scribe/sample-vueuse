[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 1 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 2 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `data` | `number` | let/var | `shallowRef<number[] | null>(null)` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `baseSort` | nextTick() | *none* |
| async-function | `workerSort` | nextTick(), workerFn() | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


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