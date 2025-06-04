[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 8 |
| 🟢 Vue Composition API | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useSpeechRecognition/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useSpeechRecognition` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `watch` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `i` | `number` | let/var | `arr.length` | ✗ |
| `temp` | `T` | let/var | `*not shown*` | ✗ |
| `index` | `number` | let/var | `*not shown*` | ✗ |
| `colors` | `string[]` | let/var | `['aqua', 'azure', 'beige', 'bisque', 'black', 'blue', 'brown', 'chocolate', 'coral', 'crimson', 'cyan', 'fuchsia', 'ghostwhite', 'gold', 'goldenrod', 'gray', 'green', 'indigo', 'ivory', 'khaki', 'lavender', 'lime', 'linen', 'magenta', 'maroon', 'moccasin', 'navy', 'olive', 'orange', 'orchid', 'peru', 'pink', 'plum', 'purple', 'red', 'salmon', 'sienna', 'silver', 'snow', 'tan', 'teal', 'thistle', 'tomato', 'turquoise', 'violet', 'white', 'yellow', 'transparent']` | ✗ |
| `grammar` | `string` | let/var | ``#JSGF V1.0; grammar colors; public <color> = ${colors.join(' | ')} ;`` | ✗ |
| `SpeechGrammarList` | `any` | let/var | `window.SpeechGrammarList || window.webkitSpeechGrammarList` | ✗ |
| `speechRecognitionList` | `any` | let/var | `new SpeechGrammarList()` | ✗ |
| `sampled` | `boolean` | let/var | `shallowRef<string[]>([])` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `sample(arr: T[], size: number): T[]`

<details><summary>Code</summary>

```ts
function sample<T>(arr: T[], size: number) {
  const shuffled = arr.slice(0)
  let i = arr.length
  let temp: T
  let index: number
  while (i--) {
    index = Math.floor((i + 1) * Math.random())
    temp = shuffled[index]
    shuffled[index] = shuffled[i]
    shuffled[i] = temp
  }
  return shuffled.slice(0, size)
}
```
</details>

- **Parameters**:
  - `arr: T[]`
  - `size: number`
- **Return Type**: `T[]`
- **Calls**:
  - `arr.slice`
  - `Math.floor`
  - `Math.random`
  - `shuffled.slice`
### `start(): void`

<details><summary>Code</summary>

```ts
function start() {
  color.value = 'transparent'
  speech.result.value = ''
  sampled.value = sample(colors, 5)
  speech.start()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `sample`
  - `speech.start`

---