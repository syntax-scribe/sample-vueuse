[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useMediaControls/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `reactify` | `@vueuse/core` |
| `useMediaControls` | `@vueuse/core` |
| `computed` | `vue` |
| `reactive` | `vue` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |
| `YAML` | `yaml` |
| `Menu` | `./components/Menu.vue` |
| `MenuItem` | `./components/MenuItem.vue` |
| `Scrubber` | `./components/Scrubber.vue` |
| `Spinner` | `./components/Spinner.vue` |


---

## Functions

### `formatDuration(seconds: number): string`

<details><summary>Code</summary>

```ts
function formatDuration(seconds: number) {
  return new Date(1000 * seconds).toISOString().slice(14, 19)
}
```
</details>

- **Parameters**:
  - `seconds: number`
- **Return Type**: `string`
- **Calls**:
  - `new Date(1000 * seconds).toISOString().slice`

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