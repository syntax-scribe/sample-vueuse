[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 5 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useGamepad/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `ConfigurableWindow` | `../_configurable` |
| `createEventHook` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useRafFn` | `../useRafFn` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `hapticActuators` | `any[]` | const | `[]` | ✗ |
| `vibrationActuator` | `any` | const | `'vibrationActuator' in gamepad ? (gamepad as any).vibrationActuator : null` | ✗ |
| `_gamepads` | `Gamepad[]` | const | `navigator?.getGamepads() || []` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |
| `_gamepads` | `Gamepad[]` | const | `navigator?.getGamepads() || []` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |


---

## Functions

### `mapGamepadToXbox360Controller(gamepad: Ref<Gamepad | undefined>): any`

<details><summary>Code</summary>

```ts
export function mapGamepadToXbox360Controller(gamepad: Ref<Gamepad | undefined>) {
  return computed(() => {
    if (gamepad.value) {
      return {
        buttons: {
          a: gamepad.value.buttons[0],
          b: gamepad.value.buttons[1],
          x: gamepad.value.buttons[2],
          y: gamepad.value.buttons[3],
        },
        bumper: {
          left: gamepad.value.buttons[4],
          right: gamepad.value.buttons[5],
        },
        triggers: {
          left: gamepad.value.buttons[6],
          right: gamepad.value.buttons[7],
        },
        stick: {
          left: {
            horizontal: gamepad.value.axes[0],
            vertical: gamepad.value.axes[1],
            button: gamepad.value.buttons[10],
          },
          right: {
            horizontal: gamepad.value.axes[2],
            vertical: gamepad.value.axes[3],
            button: gamepad.value.buttons[11],
          },
        },
        dpad: {
          up: gamepad.value.buttons[12],
          down: gamepad.value.buttons[13],
          left: gamepad.value.buttons[14],
          right: gamepad.value.buttons[15],
        },
        back: gamepad.value.buttons[8],
        start: gamepad.value.buttons[9],
      }
    }

    return null
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Maps a standard standard gamepad to an Xbox 360 Controller.
 */
```

- **Parameters**:
  - `gamepad: Ref<Gamepad | undefined>`
- **Return Type**: `any`
- **Calls**:
  - `computed (from vue)`
### `useGamepad(options: UseGamepadOptions): { isSupported: any; onConnected: any; onDisconnected: any; gamepads: any; pause: Pausable; resume: Pausable; isActive: Pausable; }`

<details><summary>Code</summary>

```ts
export function useGamepad(options: UseGamepadOptions = {}) {
  const {
    navigator = defaultNavigator,
  } = options
  const isSupported = useSupported(() => navigator && 'getGamepads' in navigator)
  const gamepads = deepRef<Gamepad[]>([])

  const onConnectedHook = createEventHook<number>()
  const onDisconnectedHook = createEventHook<number>()

  const stateFromGamepad = (gamepad: Gamepad) => {
    const hapticActuators = []
    const vibrationActuator = 'vibrationActuator' in gamepad ? (gamepad as any).vibrationActuator : null

    if (vibrationActuator)
      hapticActuators.push(vibrationActuator)

    // @ts-expect-error missing in types
    if (gamepad.hapticActuators)
      // @ts-expect-error missing in types
      hapticActuators.push(...gamepad.hapticActuators)

    return {
      id: gamepad.id,
      index: gamepad.index,
      connected: gamepad.connected,
      mapping: gamepad.mapping,
      timestamp: gamepad.timestamp,
      vibrationActuator: gamepad.vibrationActuator,
      hapticActuators,
      axes: gamepad.axes.map(axes => axes),
      buttons: gamepad.buttons.map(button => ({ pressed: button.pressed, touched: button.touched, value: button.value })),
    } as Gamepad
  }

  const updateGamepadState = () => {
    const _gamepads = navigator?.getGamepads() || []

    for (const gamepad of _gamepads) {
      if (gamepad && gamepads.value[gamepad.index])
        gamepads.value[gamepad.index] = stateFromGamepad(gamepad)
    }
  }

  const { isActive, pause, resume } = useRafFn(updateGamepadState)

  const onGamepadConnected = (gamepad: Gamepad) => {
    if (!gamepads.value.some(({ index }) => index === gamepad.index)) {
      gamepads.value.push(stateFromGamepad(gamepad))
      onConnectedHook.trigger(gamepad.index)
    }

    resume()
  }

  const onGamepadDisconnected = (gamepad: Gamepad) => {
    gamepads.value = gamepads.value.filter(x => x.index !== gamepad.index)
    onDisconnectedHook.trigger(gamepad.index)
  }

  const listenerOptions = { passive: true }
  useEventListener('gamepadconnected', e => onGamepadConnected(e.gamepad), listenerOptions)
  useEventListener('gamepaddisconnected', e => onGamepadDisconnected(e.gamepad), listenerOptions)

  tryOnMounted(() => {
    const _gamepads = navigator?.getGamepads() || []

    for (const gamepad of _gamepads) {
      if (gamepad && gamepads.value[gamepad.index])
        onGamepadConnected(gamepad)
    }
  })

  pause()

  return {
    isSupported,
    onConnected: onConnectedHook.on,
    onDisconnected: onDisconnectedHook.on,
    gamepads,
    pause,
    resume,
    isActive,
  }
}
```
</details>

- **Parameters**:
  - `options: UseGamepadOptions`
- **Return Type**: `{ isSupported: any; onConnected: any; onDisconnected: any; gamepads: any; pause: Pausable; resume: Pausable; isActive: Pausable; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `deepRef (from vue)`
  - `createEventHook (from @vueuse/shared)`
  - `hapticActuators.push`
  - `gamepad.axes.map`
  - `gamepad.buttons.map`
  - `navigator?.getGamepads`
  - `stateFromGamepad`
  - `useRafFn (from ../useRafFn)`
  - `gamepads.value.some`
  - `gamepads.value.push`
  - `onConnectedHook.trigger`
  - `resume`
  - `gamepads.value.filter`
  - `onDisconnectedHook.trigger`
  - `useEventListener (from ../useEventListener)`
  - `onGamepadConnected`
  - `onGamepadDisconnected`
  - `tryOnMounted (from @vueuse/shared)`
  - `pause`
- **Internal Comments**:
```
// @ts-expect-error missing in types (x5)
```

### `stateFromGamepad(gamepad: Gamepad): Gamepad`

<details><summary>Code</summary>

```ts
(gamepad: Gamepad) => {
    const hapticActuators = []
    const vibrationActuator = 'vibrationActuator' in gamepad ? (gamepad as any).vibrationActuator : null

    if (vibrationActuator)
      hapticActuators.push(vibrationActuator)

    // @ts-expect-error missing in types
    if (gamepad.hapticActuators)
      // @ts-expect-error missing in types
      hapticActuators.push(...gamepad.hapticActuators)

    return {
      id: gamepad.id,
      index: gamepad.index,
      connected: gamepad.connected,
      mapping: gamepad.mapping,
      timestamp: gamepad.timestamp,
      vibrationActuator: gamepad.vibrationActuator,
      hapticActuators,
      axes: gamepad.axes.map(axes => axes),
      buttons: gamepad.buttons.map(button => ({ pressed: button.pressed, touched: button.touched, value: button.value })),
    } as Gamepad
  }
```
</details>

- **Parameters**:
  - `gamepad: Gamepad`
- **Return Type**: `Gamepad`
- **Calls**:
  - `hapticActuators.push`
  - `gamepad.axes.map`
  - `gamepad.buttons.map`
- **Internal Comments**:
```
// @ts-expect-error missing in types (x5)
```

### `updateGamepadState(): void`

<details><summary>Code</summary>

```ts
() => {
    const _gamepads = navigator?.getGamepads() || []

    for (const gamepad of _gamepads) {
      if (gamepad && gamepads.value[gamepad.index])
        gamepads.value[gamepad.index] = stateFromGamepad(gamepad)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `navigator?.getGamepads`
  - `stateFromGamepad`
### `onGamepadConnected(gamepad: Gamepad): void`

<details><summary>Code</summary>

```ts
(gamepad: Gamepad) => {
    if (!gamepads.value.some(({ index }) => index === gamepad.index)) {
      gamepads.value.push(stateFromGamepad(gamepad))
      onConnectedHook.trigger(gamepad.index)
    }

    resume()
  }
```
</details>

- **Parameters**:
  - `gamepad: Gamepad`
- **Return Type**: `void`
- **Calls**:
  - `gamepads.value.some`
  - `gamepads.value.push`
  - `stateFromGamepad`
  - `onConnectedHook.trigger`
  - `resume`
### `onGamepadDisconnected(gamepad: Gamepad): void`

<details><summary>Code</summary>

```ts
(gamepad: Gamepad) => {
    gamepads.value = gamepads.value.filter(x => x.index !== gamepad.index)
    onDisconnectedHook.trigger(gamepad.index)
  }
```
</details>

- **Parameters**:
  - `gamepad: Gamepad`
- **Return Type**: `void`
- **Calls**:
  - `gamepads.value.filter`
  - `onDisconnectedHook.trigger`

---

## Interfaces

### `UseGamepadOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseGamepadOptions extends ConfigurableWindow, ConfigurableNavigator {

}
```
</details>


---

## Type Aliases

### `UseGamepadReturn`

```ts
type UseGamepadReturn = ReturnType<typeof useGamepad>;
```


---