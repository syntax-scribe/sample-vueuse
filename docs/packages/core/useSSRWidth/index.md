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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `ssrWidthSymbol` | `InjectionKey<number>` | const | `Symbol('vueuse-ssr-width') as InjectionKey<number | null>` | ✗ |
| `ssrWidth` | `any` | const | `hasInjectionContext() ? injectLocal(ssrWidthSymbol, null) : null` | ✗ |


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