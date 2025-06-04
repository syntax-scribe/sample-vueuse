[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 12 |
| 📊 Variables & Constants | 8 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useCssVar/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `defaultWindow` | `@vueuse/core` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `nextTick` | `vue` |
| `onMounted` | `vue` |
| `shallowRef` | `vue` |
| `useTemplateRef` | `vue` |
| `mount` | `../../.test` |
| `useCssVar` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `color` | `"--color"` | const | `'--color'` | ✗ |
| `color` | `"--color"` | const | `'--color'` | ✗ |
| `property` | `"--color"` | let/var | `'--color'` | ✗ |
| `window` | `any` | let/var | `defaultWindow` | ✗ |
| `color` | `"--color"` | let/var | `'--color'` | ✗ |
| `color` | `"--color"` | const | `'--color'` | ✗ |
| `color` | `"--color"` | const | `'--color'` | ✗ |
| `color` | `"--color"` | const | `'--color'` | ✗ |


---

## Functions

### `switchTarget(): void`

<details><summary>Code</summary>

```ts
function switchTarget() {
          if (target.value === el.value)
            target.value = el2.value
          else
            target.value = el.value
        }
```
</details>

- **Return Type**: `void`
### `changeVar(): void`

<details><summary>Code</summary>

```ts
function changeVar() {
          if (key.value === '--color')
            key.value = '--color-one'
          else
            key.value = '--color'
        }
```
</details>

- **Return Type**: `void`

---