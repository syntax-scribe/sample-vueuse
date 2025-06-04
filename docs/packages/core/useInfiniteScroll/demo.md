[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useInfiniteScroll/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useInfiniteScroll` | `@vueuse/core` |
| `deepRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `el` | `boolean` | let/var | `useTemplateRef<HTMLElement>('el')` | ✗ |
| `data` | `boolean` | let/var | `deepRef<number[]>([])` | ✗ |
| `length` | `any` | let/var | `data.value.length + 1` | ✗ |


---

## Functions

### `canLoadMore(): boolean`

<details><summary>Code</summary>

```ts
() => {
      // inidicate when there is no more content to load so onLoadMore stops triggering
      // if (noMoreContent) return false
      return true // for demo purposes
    }
```
</details>

- **Return Type**: `boolean`
- **Internal Comments**:
```
// inidicate when there is no more content to load so onLoadMore stops triggering
// if (noMoreContent) return false
```

### `canLoadMore(): boolean`

<details><summary>Code</summary>

```ts
() => {
      // inidicate when there is no more content to load so onLoadMore stops triggering
      // if (noMoreContent) return false
      return true // for demo purposes
    }
```
</details>

- **Return Type**: `boolean`
- **Internal Comments**:
```
// inidicate when there is no more content to load so onLoadMore stops triggering
// if (noMoreContent) return false
```

### `resetList(): void`

<details><summary>Code</summary>

```ts
function resetList() {
  data.value = []
  reset()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `reset`

---