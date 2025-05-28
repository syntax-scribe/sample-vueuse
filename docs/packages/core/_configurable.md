[⬅️ Back to Table of Contents](../../index.md)

# 📄 `_configurable.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 1 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 6 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/_configurable.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `isClient` | `@vueuse/shared` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `defaultWindow` | `Window & typeof globalThis` | const | `isClient ? window : undefined` | ✓ |
| `defaultDocument` | `Document` | const | `isClient ? window.document : undefined` | ✓ |
| `defaultNavigator` | `Navigator` | const | `isClient ? window.navigator : undefined` | ✓ |
| `defaultLocation` | `Location` | const | `isClient ? window.location : undefined` | ✓ |


---

## 🔧 Functions

> No functions found in this file.


---

## Interfaces

### `ConfigurableWindow`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableWindow {
  /*
   * Specify a custom `window` instance, e.g. working with iframes or in testing environments.
   */
  window?: Window
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `window` | `Window` | ✓ |  |

### `ConfigurableDocument`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableDocument {
  /*
   * Specify a custom `document` instance, e.g. working with iframes or in testing environments.
   */
  document?: Document
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `document` | `Document` | ✓ |  |

### `ConfigurableDocumentOrShadowRoot`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableDocumentOrShadowRoot {
  /*
   * Specify a custom `document` instance or a shadow root, e.g. working with iframes or in testing environments.
   */
  document?: DocumentOrShadowRoot
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `document` | `DocumentOrShadowRoot` | ✓ |  |

### `ConfigurableNavigator`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableNavigator {
  /*
   * Specify a custom `navigator` instance, e.g. working with iframes or in testing environments.
   */
  navigator?: Navigator
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `navigator` | `Navigator` | ✓ |  |

### `ConfigurableLocation`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableLocation {
  /*
   * Specify a custom `location` instance, e.g. working with iframes or in testing environments.
   */
  location?: Location
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `location` | `Location` | ✓ |  |

### `ConfigurableDeepRefs<D extends boolean>`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableDeepRefs<D extends boolean> {
  /**
   * Return deep refs instead of shallow refs.
   *
   * @default true - will be changed to `false` by default in the next major
   */
  deepRefs?: D
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `deepRefs` | `D` | ✓ |  |


---