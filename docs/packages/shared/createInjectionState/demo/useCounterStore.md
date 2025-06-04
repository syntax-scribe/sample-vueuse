[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `useCounterStore.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 5 |
| 📦 Imports | 4 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/shared/createInjectionState/demo/useCounterStore.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `computed` | `vue` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `createInjectionState` | `../../createInjectionState` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `increment(): void`

<details><summary>Code</summary>

```ts
function increment() {
    count.value++
  }
```
</details>

- **Return Type**: `void`
### `useCounterStoreWithDefaultValue(): { count: any; double: any; increment: () => void; }`

<details><summary>Code</summary>

```ts
export function useCounterStoreWithDefaultValue() {
  return useCounterStore() ?? {
    count: shallowRef(0),
    double: shallowRef(0),
    increment: () => {},
  }
}
```
</details>

- **Return Type**: `{ count: any; double: any; increment: () => void; }`
- **Calls**:
  - `useCounterStore`
  - `shallowRef (from vue)`
### `increment(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`
### `increment(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`
### `useCounterStoreOrThrow(): { count: any; double: any; increment: () => void; }`

<details><summary>Code</summary>

```ts
export function useCounterStoreOrThrow() {
  const counterStore = useCounterStore()
  if (counterStore == null)
    throw new Error('Please call `useProvideCounterStore` on the appropriate parent component')
  return counterStore
}
```
</details>

- **Return Type**: `{ count: any; double: any; increment: () => void; }`
- **Calls**:
  - `useCounterStore`

---