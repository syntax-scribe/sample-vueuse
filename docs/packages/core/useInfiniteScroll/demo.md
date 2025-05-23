[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useInfiniteScroll/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useInfiniteScroll` | `@vueuse/core` |
| `deepRef` | `vue` |
| `useTemplateRef` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---