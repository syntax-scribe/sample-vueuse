[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/provideLocal/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `InjectionKey` | `vue` |
| `getCurrentInstance` | `vue` |
| `provide` | `vue` |
| `localProvidedStateMap` | `./map` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `instance` | `any` | const | `getCurrentInstance()?.proxy` | ✗ |
| `localProvidedState` | `Record<string | symbol, any>` | const | `localProvidedStateMap.get(instance)!` | ✗ |


---

## Functions

### `provideLocal(key: K, value: K extends InjectionKey<infer V> ? V : T): ProvideLocalReturn`

<details><summary>Code</summary>

```ts
export function provideLocal<T, K = InjectionKey<T> | string | number>(key: K, value: K extends InjectionKey<infer V> ? V : T): ProvideLocalReturn {
  const instance = getCurrentInstance()?.proxy
  if (instance == null)
    throw new Error('provideLocal must be called in setup')

  if (!localProvidedStateMap.has(instance))
    localProvidedStateMap.set(instance, Object.create(null))

  const localProvidedState = localProvidedStateMap.get(instance)!
  // @ts-expect-error allow InjectionKey as key
  localProvidedState[key] = value
  return provide<T, K>(key, value)
}
```
</details>

- **JSDoc**:
```ts
/**
 * On the basis of `provide`, it is allowed to directly call inject to obtain the value after call provide in the same component.
 *
 * @example
 * ```ts
 * provideLocal('MyInjectionKey', 1)
 * const injectedValue = injectLocal('MyInjectionKey') // injectedValue === 1
 * ```
 */
```

- **Parameters**:
  - `key: K`
  - `value: K extends InjectionKey<infer V> ? V : T`
- **Return Type**: `ProvideLocalReturn`
- **Calls**:
  - `getCurrentInstance (from vue)`
  - `localProvidedStateMap.has`
  - `localProvidedStateMap.set`
  - `Object.create`
  - `localProvidedStateMap.get`
  - `provide (from vue)`
- **Internal Comments**:
```
// @ts-expect-error allow InjectionKey as key (x4)
```


---

## Type Aliases

### `ProvideLocalReturn`

```ts
type ProvideLocalReturn = void;
```


---