[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `voice` | `boolean` | let/var | `deepRef<SpeechSynthesisVoice>(undefined as unknown as SpeechSynthesisVoice)` | ✗ |
| `synth` | `SpeechSynthesis` | let/var | `*not shown*` | ✗ |
| `voices` | `boolean` | let/var | `shallowRef<SpeechSynthesisVoice[]>([])` | ✗ |


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