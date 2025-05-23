[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useSSRWidth/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `App` | `vue` |
| `InjectionKey` | `vue` |
| `injectLocal` | `@vueuse/shared` |
| `provideLocal` | `@vueuse/shared` |
| `hasInjectionContext` | `vue` |


---

## Functions

### `useSSRWidth(): number`

<details><summary>Code</summary>

```ts
export function useSSRWidth() {
  // Avoid injection warning outside of components
  const ssrWidth = hasInjectionContext() ? injectLocal(ssrWidthSymbol, null) : null
  return typeof ssrWidth === 'number' ? ssrWidth : undefined
}
```
</details>

- **Return Type**: `number`
- **Calls**:
  - `hasInjectionContext (from vue)`
  - `injectLocal (from @vueuse/shared)`
- **Internal Comments**:
```
// Avoid injection warning outside of components (x2)
```

### `provideSSRWidth(width: number | null, app: App<unknown>): void`

<details><summary>Code</summary>

```ts
export function provideSSRWidth(width: number | null, app?: App<unknown>) {
  if (app !== undefined) {
    app.provide(ssrWidthSymbol, width)
  }
  else {
    provideLocal(ssrWidthSymbol, width)
  }
}
```
</details>

- **Parameters**:
  - `width: number | null`
  - `app: App<unknown>`
- **Return Type**: `void`
- **Calls**:
  - `app.provide`
  - `provideLocal (from @vueuse/shared)`

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