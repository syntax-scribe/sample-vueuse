[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
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
📂 **`packages/shared/injectLocal/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `getCurrentInstance` | `vue` |
| `hasInjectionContext` | `vue` |
| `inject` | `vue` |
| `localProvidedStateMap` | `../provideLocal/map` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `key` | `string | symbol` | const | `args[0] as string | symbol` | ✗ |
| `instance` | `any` | const | `getCurrentInstance()?.proxy` | ✗ |


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