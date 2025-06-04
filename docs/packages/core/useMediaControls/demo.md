[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `video` | `boolean` | let/var | `useTemplateRef<HTMLVideoElement>('video')` | ✗ |
| `poster` | `"https://cdn.bitmovin.com/content/assets/sintel/poster.png"` | let/var | `'https://cdn.bitmovin.com/content/assets/sintel/poster.png'` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `reactive` | reactive | *none* | *none* |
| `computed` | computed | *none* | *none* |


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