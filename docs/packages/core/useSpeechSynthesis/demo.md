[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useSpeechSynthesis/demo.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `useSpeechSynthesis` | `@vueuse/core` |
| `deepRef` | `vue` |
| `onMounted` | `vue` |
| `shallowRef` | `vue` |


---

## Functions

### `play(): void`

<details><summary>Code</summary>

```ts
function play() {
  if (speech.status.value === 'pause') {
    console.log('resume')
    window.speechSynthesis.resume()
  }
  else {
    speech.speak()
  }
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `console.log`
  - `window.speechSynthesis.resume`
  - `speech.speak`
### `pause(): void`

<details><summary>Code</summary>

```ts
function pause() {
  window.speechSynthesis.pause()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `window.speechSynthesis.pause`
### `stop(): void`

<details><summary>Code</summary>

```ts
function stop() {
  speech.stop()
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `speech.stop`

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