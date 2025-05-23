[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 3
- **Interfaces**: 1
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/createInjectionState/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `InjectionKey` | `vue` |
| `injectLocal` | `../injectLocal` |
| `provideLocal` | `../provideLocal` |


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

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---