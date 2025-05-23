[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 3
- **Classes**: 0
- **Imports**: 5
- **Interfaces**: 0
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useScreenSafeArea/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `isClient` | `@vueuse/shared` |
| `useDebounceFn` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `useCssVar` | `../useCssVar` |
| `useEventListener` | `../useEventListener` |


---

## Functions

### `useScreenSafeArea(): { top: any; right: any; bottom: any; left: any; update: () => void; }`

<details><summary>Code</summary>

```ts
export function useScreenSafeArea() {
  const top = shallowRef('')
  const right = shallowRef('')
  const bottom = shallowRef('')
  const left = shallowRef('')

  if (isClient) {
    const topCssVar = useCssVar(topVarName)
    const rightCssVar = useCssVar(rightVarName)
    const bottomCssVar = useCssVar(bottomVarName)
    const leftCssVar = useCssVar(leftVarName)

    topCssVar.value = 'env(safe-area-inset-top, 0px)'
    rightCssVar.value = 'env(safe-area-inset-right, 0px)'
    bottomCssVar.value = 'env(safe-area-inset-bottom, 0px)'
    leftCssVar.value = 'env(safe-area-inset-left, 0px)'

    update()

    useEventListener('resize', useDebounceFn(update), { passive: true })
  }

  function update() {
    top.value = getValue(topVarName)
    right.value = getValue(rightVarName)
    bottom.value = getValue(bottomVarName)
    left.value = getValue(leftVarName)
  }

  return {
    top,
    right,
    bottom,
    left,
    update,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive `env(safe-area-inset-*)`
 *
 * @see https://vueuse.org/useScreenSafeArea
 */
```

- **Return Type**: `{ top: any; right: any; bottom: any; left: any; update: () => void; }`
- **Calls**:
  - `shallowRef (from vue)`
  - `useCssVar (from ../useCssVar)`
  - `update`
  - `useEventListener (from ../useEventListener)`
  - `useDebounceFn (from @vueuse/shared)`
  - `getValue`
### `update(): void`

<details><summary>Code</summary>

```ts
function update() {
    top.value = getValue(topVarName)
    right.value = getValue(rightVarName)
    bottom.value = getValue(bottomVarName)
    left.value = getValue(leftVarName)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `getValue`
### `getValue(position: VarName): string`

<details><summary>Code</summary>

```ts
function getValue(position: VarName) {
  return getComputedStyle(document.documentElement).getPropertyValue(position)
}
```
</details>

- **Parameters**:
  - `position: VarName`
- **Return Type**: `string`
- **Calls**:
  - `getComputedStyle(document.documentElement).getPropertyValue`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `VarName`

```ts
type VarName = '--vueuse-safe-area-top' | '--vueuse-safe-area-right' | '--vueuse-safe-area-bottom' | '--vueuse-safe-area-left';
```


---