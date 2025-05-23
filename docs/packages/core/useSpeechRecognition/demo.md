[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useSpeechRecognition/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useSpeechRecognition` | `@vueuse/core` |
| `shallowRef` | `vue` |
| `watch` | `vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---