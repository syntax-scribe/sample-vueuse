[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useElementByPoint/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Pausable` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `useIntervalFn` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useRafFn` | `../useRafFn` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useElementByPoint(options: UseElementByPointOptions<M>): UseElementByPointReturn<M>`

<details><summary>Code</summary>

```ts
export function useElementByPoint<M extends boolean = false>(options: UseElementByPointOptions<M>): UseElementByPointReturn<M> {
  const {
    x,
    y,
    document = defaultDocument,
    multiple,
    interval = 'requestAnimationFrame',
    immediate = true,
  } = options

  const isSupported = useSupported(() => {
    if (toValue(multiple))
      return document && 'elementsFromPoint' in document

    return document && 'elementFromPoint' in document
  })

  const element = shallowRef<any>(null)

  const cb = () => {
    element.value = toValue(multiple)
      ? document?.elementsFromPoint(toValue(x), toValue(y)) ?? []
      : document?.elementFromPoint(toValue(x), toValue(y)) ?? null
  }

  const controls: Pausable = interval === 'requestAnimationFrame'
    ? useRafFn(cb, { immediate })
    : useIntervalFn(cb, interval, { immediate })

  return {
    isSupported,
    element,
    ...controls,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive element by point.
 *
 * @see https://vueuse.org/useElementByPoint
 * @param options - UseElementByPointOptions
 */
```

- **Parameters**:
  - `options: UseElementByPointOptions<M>`
- **Return Type**: `UseElementByPointReturn<M>`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `toValue (from vue)`
  - `shallowRef (from vue)`
  - `document?.elementsFromPoint`
  - `document?.elementFromPoint`
  - `useRafFn (from ../useRafFn)`
  - `useIntervalFn (from @vueuse/shared)`
### `cb(): void`

<details><summary>Code</summary>

```ts
() => {
    element.value = toValue(multiple)
      ? document?.elementsFromPoint(toValue(x), toValue(y)) ?? []
      : document?.elementFromPoint(toValue(x), toValue(y)) ?? null
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `toValue (from vue)`
  - `document?.elementsFromPoint`
  - `document?.elementFromPoint`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseElementByPointOptions<Multiple extends boolean = false>`

<details><summary>Interface Code</summary>

```ts
export interface UseElementByPointOptions<Multiple extends boolean = false> extends ConfigurableDocument {
  x: MaybeRefOrGetter<number>
  y: MaybeRefOrGetter<number>
  multiple?: MaybeRefOrGetter<Multiple>
  immediate?: boolean
  interval?: 'requestAnimationFrame' | number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `x` | `MaybeRefOrGetter<number>` | ✗ |  |
| `y` | `MaybeRefOrGetter<number>` | ✗ |  |
| `multiple` | `MaybeRefOrGetter<Multiple>` | ✓ |  |
| `immediate` | `boolean` | ✓ |  |
| `interval` | `'requestAnimationFrame' | number` | ✓ |  |

### `UseElementByPointReturn<Multiple extends boolean = false>`

<details><summary>Interface Code</summary>

```ts
export interface UseElementByPointReturn<Multiple extends boolean = false> extends Pausable {
  isSupported: ComputedRef<boolean>
  element: ShallowRef<Multiple extends true ? HTMLElement[] : HTMLElement | null>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `element` | `ShallowRef<Multiple extends true ? HTMLElement[] : HTMLElement | null>` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---