[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/shared/injectLocal/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `getCurrentInstance` | `vue` |
| `hasInjectionContext` | `vue` |
| `inject` | `vue` |
| `localProvidedStateMap` | `../provideLocal/map` |


---

## Functions

### `injectLocal(args: any[]): any`

<details><summary>Code</summary>

```ts
(...args) => {
  const key = args[0] as string | symbol
  const instance = getCurrentInstance()?.proxy
  if (instance == null && !hasInjectionContext())
    throw new Error('injectLocal must be called in setup')

  if (instance && localProvidedStateMap.has(instance) && key in localProvidedStateMap.get(instance)!)
    return localProvidedStateMap.get(instance)![key]

  // @ts-expect-error overloads are not compatible
  return inject(...args)
}
```
</details>

- **Parameters**:
  - `args: any[]`
- **Return Type**: `any`
- **Calls**:
  - `getCurrentInstance (from vue)`
  - `hasInjectionContext (from vue)`
  - `localProvidedStateMap.has`
  - `localProvidedStateMap.get`
  - `inject (from vue)`
- **Internal Comments**:
```
// @ts-expect-error overloads are not compatible
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