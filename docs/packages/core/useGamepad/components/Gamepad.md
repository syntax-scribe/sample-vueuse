[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `Gamepad.vue`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 2 |
| 🟢 Vue Composition API | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useGamepad/components/Gamepad.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `computed` | `vue` |
| `Controller` | `./Controller.vue` |
| `Item` | `./Item.vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `props` | `boolean` | let/var | `defineProps<{ gamepad: Gamepad }>()` | ✗ |
| `actuator` | `any` | let/var | `props.gamepad.hapticActuators[0]` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `vibrate(): void`

<details><summary>Code</summary>

```ts
function vibrate() {
  if (supportsVibration.value) {
    // @ts-expect-error: hapticActuators is not in the Gamepad type
    const actuator: any = props.gamepad.hapticActuators[0]
    actuator.playEffect('dual-rumble', {
      startDelay: 0,
      duration: 1000,
      weakMagnitude: 1,
      strongMagnitude: 1,
    })
  }
}
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `actuator.playEffect`
- **Internal Comments**:
```
// @ts-expect-error: hapticActuators is not in the Gamepad type (x2)
```


---