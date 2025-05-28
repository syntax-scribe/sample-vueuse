[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 3 |
| 📊 Variables & Constants | 2 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/shared/createInjectionState/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `InjectionKey` | `vue` |
| `injectLocal` | `../injectLocal` |
| `provideLocal` | `../provideLocal` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `key` | `string | InjectionKey<Return>` | const | `options?.injectionKey || Symbol(composable.name || 'InjectionState')` | ✗ |
| `defaultValue` | `Return` | const | `options?.defaultValue` | ✗ |


---

## Functions

### `createInjectionState(composable: (...args: Arguments) => Return, options: CreateInjectionStateOptions<Return>): readonly [useProvidingState: (...args: Arguments) => Return, useInjectedState: () => Return | undefined]`

<details><summary>Code</summary>

```ts
export function createInjectionState<Arguments extends Array<any>, Return>(
  composable: (...args: Arguments) => Return,
  options?: CreateInjectionStateOptions<Return>,
): readonly [useProvidingState: (...args: Arguments) => Return, useInjectedState: () => Return | undefined] {
  const key: string | InjectionKey<Return> = options?.injectionKey || Symbol(composable.name || 'InjectionState')
  const defaultValue = options?.defaultValue
  const useProvidingState = (...args: Arguments) => {
    const state = composable(...args)
    provideLocal(key, state)
    return state
  }
  const useInjectedState = () => injectLocal(key, defaultValue)
  return [useProvidingState, useInjectedState]
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create global state that can be injected into components.
 *
 * @see https://vueuse.org/createInjectionState
 *
 */
```

- **Parameters**:
  - `composable: (...args: Arguments) => Return`
  - `options: CreateInjectionStateOptions<Return>`
- **Return Type**: `readonly [useProvidingState: (...args: Arguments) => Return, useInjectedState: () => Return | undefined]`
- **Calls**:
  - `Symbol`
  - `composable`
  - `provideLocal (from ../provideLocal)`
  - `injectLocal (from ../injectLocal)`
### `useProvidingState(args: Arguments): Return`

<details><summary>Code</summary>

```ts
(...args: Arguments) => {
    const state = composable(...args)
    provideLocal(key, state)
    return state
  }
```
</details>

- **Parameters**:
  - `args: Arguments`
- **Return Type**: `Return`
- **Calls**:
  - `composable`
  - `provideLocal (from ../provideLocal)`
### `useInjectedState(): any`

<details><summary>Code</summary>

```ts
() => injectLocal(key, defaultValue)
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `injectLocal (from ../injectLocal)`

---

## Interfaces

### `CreateInjectionStateOptions<Return>`

<details><summary>Interface Code</summary>

```ts
export interface CreateInjectionStateOptions<Return> {
  /**
   * Custom injectionKey for InjectionState
   */
  injectionKey?: string | InjectionKey<Return>
  /**
   * Default value for the InjectionState
   */
  defaultValue?: Return
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `injectionKey` | `string | InjectionKey<Return>` | ✓ |  |
| `defaultValue` | `Return` | ✓ |  |


---