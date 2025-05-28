[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `demo.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

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