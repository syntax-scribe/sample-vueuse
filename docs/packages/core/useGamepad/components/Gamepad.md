[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `Gamepad.vue`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useGamepad/components/Gamepad.vue`**

## 📦 Imports

| Name | Source |
|------|--------|
| `computed` | `vue` |
| `Controller` | `./Controller.vue` |
| `Item` | `./Item.vue` |


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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---