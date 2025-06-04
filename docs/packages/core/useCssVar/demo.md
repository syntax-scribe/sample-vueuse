[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useCssVar/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useCssVar` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |


---

## Functions

### `switchColor(): void`

<details><summary>Code</summary>

```ts
function switchColor() {
  if (color.value === '#df8543')
    color.value = '#7fa998'
  else
    color.value = '#df8543'
}
```
</details>

- **Return Type**: `void`
### `changeVar(): void`

<details><summary>Code</summary>

```ts
function changeVar() {
  if (key.value === '--color')
    key.value = '--color-one'
  else
    key.value = '--color'
}
```
</details>

- **Return Type**: `void`

---