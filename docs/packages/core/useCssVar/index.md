[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 10 |
| 🟢 Vue Composition API | 3 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useCssVar/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useMutationObserver` | `../useMutationObserver` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `useCssVar(prop: MaybeRefOrGetter<string | null | undefined>, target: MaybeElementRef, options: UseCssVarOptions): any`

<details><summary>Code</summary>

```ts
export function useCssVar(
  prop: MaybeRefOrGetter<string | null | undefined>,
  target?: MaybeElementRef,
  options: UseCssVarOptions = {},
) {
  const { window = defaultWindow, initialValue, observe = false } = options
  const variable = shallowRef(initialValue)
  const elRef = computed(() => unrefElement(target) || window?.document?.documentElement)

  function updateCssVar() {
    const key = toValue(prop)
    const el = toValue(elRef)
    if (el && window && key) {
      const value = window.getComputedStyle(el).getPropertyValue(key)?.trim()
      variable.value = value || variable.value || initialValue
    }
  }

  if (observe) {
    useMutationObserver(elRef, updateCssVar, {
      attributeFilter: ['style', 'class'],
      window,
    })
  }

  watch(
    [elRef, () => toValue(prop)],
    (_, old) => {
      if (old[0] && old[1])
        old[0].style.removeProperty(old[1])
      updateCssVar()
    },
    { immediate: true },
  )

  watch(
    [variable, elRef],
    ([val, el]) => {
      const raw_prop = toValue(prop)
      if (el?.style && raw_prop) {
        if (val == null)
          el.style.removeProperty(raw_prop)
        else
          el.style.setProperty(raw_prop, val)
      }
    },
    { immediate: true },
  )

  return variable
}
```
</details>

- **JSDoc**:
```ts
/**
 * Manipulate CSS variables.
 *
 * @see https://vueuse.org/useCssVar
 * @param prop
 * @param target
 * @param options
 */
```

- **Parameters**:
  - `prop: MaybeRefOrGetter<string | null | undefined>`
  - `target: MaybeElementRef`
  - `options: UseCssVarOptions`
- **Return Type**: `any`
- **Calls**:
  - `shallowRef (from vue)`
  - `computed (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `toValue (from vue)`
  - `window.getComputedStyle(el).getPropertyValue(key)?.trim`
  - `useMutationObserver (from ../useMutationObserver)`
  - `watch (from vue)`
  - `old[0].style.removeProperty`
  - `updateCssVar`
  - `el.style.removeProperty`
  - `el.style.setProperty`
### `updateCssVar(): void`

<details><summary>Code</summary>

```ts
function updateCssVar() {
    const key = toValue(prop)
    const el = toValue(elRef)
    if (el && window && key) {
      const value = window.getComputedStyle(el).getPropertyValue(key)?.trim()
      variable.value = value || variable.value || initialValue
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `window.getComputedStyle(el).getPropertyValue(key)?.trim`

---

## Interfaces

### `UseCssVarOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseCssVarOptions extends ConfigurableWindow {
  initialValue?: string
  /**
   * Use MutationObserver to monitor variable changes
   * @default false
   */
  observe?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialValue` | `string` | ✓ |  |
| `observe` | `boolean` | ✓ |  |


---