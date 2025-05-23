[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `ProvideLocalReturn`

```ts
type ProvideLocalReturn = void;
```


---