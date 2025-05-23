[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 8
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 1
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/useBreakpoints/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `increaseWithUnit` | `@vueuse/shared` |
| `pxValue` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useMediaQuery` | `../useMediaQuery` |
| `useSSRWidth` | `../useSSRWidth` |


---

## Functions

### `useBreakpoints(breakpoints: Breakpoints<K>, options: UseBreakpointsOptions): Record<K, any> & { greaterOrEqual: (k: MaybeRefOrGetter<K>) => any; smallerOrEqual: (k: MaybeRefOrGetter<K>) => any; greater(k: MaybeRefOrGetter<K>): any; smaller(k: MaybeRefOrGetter<K>): any; between(a: MaybeRefOrGetter<K>, b: MaybeRefOrGetter<K>): any; ... 6 more ...; active(): any; }`

<details><summary>Code</summary>

```ts
export function useBreakpoints<K extends string>(
  breakpoints: Breakpoints<K>,
  options: UseBreakpointsOptions = {},
) {
  function getValue(k: MaybeRefOrGetter<K>, delta?: number) {
    let v = toValue(breakpoints[toValue(k)])

    if (delta != null)
      v = increaseWithUnit(v, delta)

    if (typeof v === 'number')
      v = `${v}px`

    return v
  }

  const { window = defaultWindow, strategy = 'min-width', ssrWidth = useSSRWidth() } = options

  const ssrSupport = typeof ssrWidth === 'number'
  const mounted = ssrSupport ? shallowRef(false) : { value: true }
  if (ssrSupport) {
    tryOnMounted(() => mounted.value = !!window)
  }

  function match(query: 'min' | 'max', size: string): boolean {
    if (!mounted.value && ssrSupport) {
      return query === 'min' ? ssrWidth >= pxValue(size) : ssrWidth <= pxValue(size)
    }
    if (!window)
      return false
    return window.matchMedia(`(${query}-width: ${size})`).matches
  }

  const greaterOrEqual = (k: MaybeRefOrGetter<K>) => {
    return useMediaQuery(() => `(min-width: ${getValue(k)})`, options)
  }

  const smallerOrEqual = (k: MaybeRefOrGetter<K>) => {
    return useMediaQuery(() => `(max-width: ${getValue(k)})`, options)
  }

  const shortcutMethods = (Object.keys(breakpoints) as K[])
    .reduce((shortcuts, k) => {
      Object.defineProperty(shortcuts, k, {
        get: () => strategy === 'min-width'
          ? greaterOrEqual(k)
          : smallerOrEqual(k),
        enumerable: true,
        configurable: true,
      })
      return shortcuts
    }, {} as Record<K, ReturnType<typeof greaterOrEqual>>)

  function current() {
    const points = (Object.keys(breakpoints) as K[])
      .map(k => [k, shortcutMethods[k], pxValue(getValue(k))] as const)
      .sort((a, b) => a[2] - b[2])
    return computed(() => points.filter(([, v]) => v.value).map(([k]) => k))
  }

  return Object.assign(shortcutMethods, {
    greaterOrEqual,
    smallerOrEqual,
    greater(k: MaybeRefOrGetter<K>) {
      return useMediaQuery(() => `(min-width: ${getValue(k, 0.1)})`, options)
    },
    smaller(k: MaybeRefOrGetter<K>) {
      return useMediaQuery(() => `(max-width: ${getValue(k, -0.1)})`, options)
    },
    between(a: MaybeRefOrGetter<K>, b: MaybeRefOrGetter<K>) {
      return useMediaQuery(() => `(min-width: ${getValue(a)}) and (max-width: ${getValue(b, -0.1)})`, options)
    },
    isGreater(k: MaybeRefOrGetter<K>) {
      return match('min', getValue(k, 0.1))
    },
    isGreaterOrEqual(k: MaybeRefOrGetter<K>) {
      return match('min', getValue(k))
    },
    isSmaller(k: MaybeRefOrGetter<K>) {
      return match('max', getValue(k, -0.1))
    },
    isSmallerOrEqual(k: MaybeRefOrGetter<K>) {
      return match('max', getValue(k))
    },
    isInBetween(a: MaybeRefOrGetter<K>, b: MaybeRefOrGetter<K>) {
      return match('min', getValue(a)) && match('max', getValue(b, -0.1))
    },
    current,
    active() {
      const bps = current()
      return computed(() => bps.value.length === 0 ? '' : bps.value.at(strategy === 'min-width' ? -1 : 0)!)
    },
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactively viewport breakpoints
 *
 * @see https://vueuse.org/useBreakpoints
 */
```

- **Parameters**:
  - `breakpoints: Breakpoints<K>`
  - `options: UseBreakpointsOptions`
- **Return Type**: `Record<K, any> & { greaterOrEqual: (k: MaybeRefOrGetter<K>) => any; smallerOrEqual: (k: MaybeRefOrGetter<K>) => any; greater(k: MaybeRefOrGetter<K>): any; smaller(k: MaybeRefOrGetter<K>): any; between(a: MaybeRefOrGetter<K>, b: MaybeRefOrGetter<K>): any; ... 6 more ...; active(): any; }`
- **Calls**:
  - `toValue (from vue)`
  - `increaseWithUnit (from @vueuse/shared)`
  - `useSSRWidth (from ../useSSRWidth)`
  - `shallowRef (from vue)`
  - `tryOnMounted (from @vueuse/shared)`
  - `pxValue (from @vueuse/shared)`
  - `window.matchMedia`
  - `useMediaQuery (from ../useMediaQuery)`
  - `getValue`
  - `(Object.keys(breakpoints) as K[])
    .reduce`
  - `Object.keys`
  - `Object.defineProperty`
  - `greaterOrEqual`
  - `smallerOrEqual`
  - `(Object.keys(breakpoints) as K[])
      .map(k => [k, shortcutMethods[k], pxValue(getValue(k))] as const)
      .sort`
  - `computed (from vue)`
  - `points.filter(([, v]) => v.value).map`
  - `Object.assign`
  - `match`
  - `current`
  - `bps.value.at`
### `getValue(k: MaybeRefOrGetter<K>, delta: number): any`

<details><summary>Code</summary>

```ts
function getValue(k: MaybeRefOrGetter<K>, delta?: number) {
    let v = toValue(breakpoints[toValue(k)])

    if (delta != null)
      v = increaseWithUnit(v, delta)

    if (typeof v === 'number')
      v = `${v}px`

    return v
  }
```
</details>

- **Parameters**:
  - `k: MaybeRefOrGetter<K>`
  - `delta: number`
- **Return Type**: `any`
- **Calls**:
  - `toValue (from vue)`
  - `increaseWithUnit (from @vueuse/shared)`
### `match(query: 'min' | 'max', size: string): boolean`

<details><summary>Code</summary>

```ts
function match(query: 'min' | 'max', size: string): boolean {
    if (!mounted.value && ssrSupport) {
      return query === 'min' ? ssrWidth >= pxValue(size) : ssrWidth <= pxValue(size)
    }
    if (!window)
      return false
    return window.matchMedia(`(${query}-width: ${size})`).matches
  }
```
</details>

- **Parameters**:
  - `query: 'min' | 'max'`
  - `size: string`
- **Return Type**: `boolean`
- **Calls**:
  - `pxValue (from @vueuse/shared)`
  - `window.matchMedia`
### `greaterOrEqual(k: MaybeRefOrGetter<K>): any`

<details><summary>Code</summary>

```ts
(k: MaybeRefOrGetter<K>) => {
    return useMediaQuery(() => `(min-width: ${getValue(k)})`, options)
  }
```
</details>

- **Parameters**:
  - `k: MaybeRefOrGetter<K>`
- **Return Type**: `any`
- **Calls**:
  - `useMediaQuery (from ../useMediaQuery)`
  - `getValue`
### `smallerOrEqual(k: MaybeRefOrGetter<K>): any`

<details><summary>Code</summary>

```ts
(k: MaybeRefOrGetter<K>) => {
    return useMediaQuery(() => `(max-width: ${getValue(k)})`, options)
  }
```
</details>

- **Parameters**:
  - `k: MaybeRefOrGetter<K>`
- **Return Type**: `any`
- **Calls**:
  - `useMediaQuery (from ../useMediaQuery)`
  - `getValue`
### `get(): any`

<details><summary>Code</summary>

```ts
() => strategy === 'min-width'
          ? greaterOrEqual(k)
          : smallerOrEqual(k)
```
</details>

- **Return Type**: `any`
### `get(): any`

<details><summary>Code</summary>

```ts
() => strategy === 'min-width'
          ? greaterOrEqual(k)
          : smallerOrEqual(k)
```
</details>

- **Return Type**: `any`
### `current(): any`

<details><summary>Code</summary>

```ts
function current() {
    const points = (Object.keys(breakpoints) as K[])
      .map(k => [k, shortcutMethods[k], pxValue(getValue(k))] as const)
      .sort((a, b) => a[2] - b[2])
    return computed(() => points.filter(([, v]) => v.value).map(([k]) => k))
  }
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `(Object.keys(breakpoints) as K[])
      .map(k => [k, shortcutMethods[k], pxValue(getValue(k))] as const)
      .sort`
  - `computed (from vue)`
  - `points.filter(([, v]) => v.value).map`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseBreakpointsOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseBreakpointsOptions extends ConfigurableWindow {
  /**
   * The query strategy to use for the generated shortcut methods like `.lg`
   *
   * 'min-width' - .lg will be true when the viewport is greater than or equal to the lg breakpoint (mobile-first)
   * 'max-width' - .lg will be true when the viewport is smaller than the xl breakpoint (desktop-first)
   *
   * @default "min-width"
   */
  strategy?: 'min-width' | 'max-width'
  ssrWidth?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `strategy` | `'min-width' | 'max-width'` | ✓ |  |
| `ssrWidth` | `number` | ✓ |  |


---

## Type Aliases

### `Breakpoints<K extends string = string extends string = string>`

```ts
type Breakpoints<K extends string = string extends string = string> = Record<K, MaybeRefOrGetter<number | string>>;
```

### `UseBreakpointsReturn<K extends string = string extends string = string>`

```ts
type UseBreakpointsReturn<K extends string = string extends string = string> = ReturnType<typeof useBreakpoints<K>>;
```


---