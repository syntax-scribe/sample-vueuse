[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 5 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 1 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useBattery/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableNavigator` | `../_configurable` |
| `shallowRef` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `events` | `string[]` | const | `['chargingchange', 'chargingtimechange', 'dischargingtimechange', 'levelchange']` | ✗ |
| `battery` | `BatteryManager | null` | let/var | `*not shown*` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `useBattery` | *none* | (navigator as NavigatorWithBattery)
      .getBattery().then |


---

## Functions

### `useBattery(options: ConfigurableNavigator): { isSupported: any; charging: any; chargingTime: any; dischargingTime: any; level: any; }`

<details><summary>Code</summary>

```ts
export function useBattery(options: ConfigurableNavigator = {}) {
  const { navigator = defaultNavigator } = options
  const events = ['chargingchange', 'chargingtimechange', 'dischargingtimechange', 'levelchange']

  const isSupported = useSupported(() => navigator && 'getBattery' in navigator && typeof navigator.getBattery === 'function')

  const charging = shallowRef(false)
  const chargingTime = shallowRef(0)
  const dischargingTime = shallowRef(0)
  const level = shallowRef(1)

  let battery: BatteryManager | null

  function updateBatteryInfo(this: BatteryManager) {
    charging.value = this.charging
    chargingTime.value = this.chargingTime || 0
    dischargingTime.value = this.dischargingTime || 0
    level.value = this.level
  }

  if (isSupported.value) {
    (navigator as NavigatorWithBattery)
      .getBattery()
      .then((_battery) => {
        battery = _battery
        updateBatteryInfo.call(battery)
        useEventListener(battery, events, updateBatteryInfo, { passive: true })
      })
  }

  return {
    isSupported,
    charging,
    chargingTime,
    dischargingTime,
    level,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Battery Status API.
 *
 * @see https://vueuse.org/useBattery
 */
```

- **Parameters**:
  - `options: ConfigurableNavigator`
- **Return Type**: `{ isSupported: any; charging: any; chargingTime: any; dischargingTime: any; level: any; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `(navigator as NavigatorWithBattery)
      .getBattery()
      .then`
  - `updateBatteryInfo.call`
  - `useEventListener (from ../useEventListener)`
### `updateBatteryInfo(this: BatteryManager): void`

<details><summary>Code</summary>

```ts
function updateBatteryInfo(this: BatteryManager) {
    charging.value = this.charging
    chargingTime.value = this.chargingTime || 0
    dischargingTime.value = this.dischargingTime || 0
    level.value = this.level
  }
```
</details>

- **Parameters**:
  - `this: BatteryManager`
- **Return Type**: `void`

---

## Interfaces

### `BatteryManager`

<details><summary>Interface Code</summary>

```ts
export interface BatteryManager extends EventTarget {
  charging: boolean
  chargingTime: number
  dischargingTime: number
  level: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `charging` | `boolean` | ✗ |  |
| `chargingTime` | `number` | ✗ |  |
| `dischargingTime` | `number` | ✗ |  |
| `level` | `number` | ✗ |  |


---

## Type Aliases

### `NavigatorWithBattery`

```ts
type NavigatorWithBattery = Navigator & {
  getBattery: () => Promise<BatteryManager>
};
```

### `UseBatteryReturn`

```ts
type UseBatteryReturn = ReturnType<typeof useBattery>;
```


---