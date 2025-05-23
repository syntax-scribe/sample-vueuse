[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 15
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 2
- **Type Aliases**: 2

## 🛠️ File Location:
📂 **`packages/core/useTransition/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `linear` | `@vueuse/shared` |
| `promiseTimeout` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Functions

### `createEasingFunction([p0, p1, p2, p3]: CubicBezierPoints): EasingFunction`

<details><summary>Code</summary>

```ts
function createEasingFunction([p0, p1, p2, p3]: CubicBezierPoints): EasingFunction {
  const a = (a1: number, a2: number) => 1 - 3 * a2 + 3 * a1
  const b = (a1: number, a2: number) => 3 * a2 - 6 * a1
  const c = (a1: number) => 3 * a1

  const calcBezier = (t: number, a1: number, a2: number) => ((a(a1, a2) * t + b(a1, a2)) * t + c(a1)) * t

  const getSlope = (t: number, a1: number, a2: number) => 3 * a(a1, a2) * t * t + 2 * b(a1, a2) * t + c(a1)

  const getTforX = (x: number) => {
    let aGuessT = x

    for (let i = 0; i < 4; ++i) {
      const currentSlope = getSlope(aGuessT, p0, p2)
      if (currentSlope === 0)
        return aGuessT
      const currentX = calcBezier(aGuessT, p0, p2) - x
      aGuessT -= currentX / currentSlope
    }

    return aGuessT
  }

  return (x: number) => (p0 === p1 && p2 === p3) ? x : calcBezier(getTforX(x), p1, p3)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create an easing function from cubic bezier points.
 */
```

- **Parameters**:
  - `[p0, p1, p2, p3]: CubicBezierPoints`
- **Return Type**: `EasingFunction`
- **Calls**:
  - `a`
  - `b`
  - `c`
  - `getSlope`
  - `calcBezier`
  - `getTforX`
### `a(a1: number, a2: number): number`

<details><summary>Code</summary>

```ts
(a1: number, a2: number) => 1 - 3 * a2 + 3 * a1
```
</details>

- **Parameters**:
  - `a1: number`
  - `a2: number`
- **Return Type**: `number`
### `b(a1: number, a2: number): number`

<details><summary>Code</summary>

```ts
(a1: number, a2: number) => 3 * a2 - 6 * a1
```
</details>

- **Parameters**:
  - `a1: number`
  - `a2: number`
- **Return Type**: `number`
### `c(a1: number): number`

<details><summary>Code</summary>

```ts
(a1: number) => 3 * a1
```
</details>

- **Parameters**:
  - `a1: number`
- **Return Type**: `number`
### `calcBezier(t: number, a1: number, a2: number): number`

<details><summary>Code</summary>

```ts
(t: number, a1: number, a2: number) => ((a(a1, a2) * t + b(a1, a2)) * t + c(a1)) * t
```
</details>

- **Parameters**:
  - `t: number`
  - `a1: number`
  - `a2: number`
- **Return Type**: `number`
### `getSlope(t: number, a1: number, a2: number): number`

<details><summary>Code</summary>

```ts
(t: number, a1: number, a2: number) => 3 * a(a1, a2) * t * t + 2 * b(a1, a2) * t + c(a1)
```
</details>

- **Parameters**:
  - `t: number`
  - `a1: number`
  - `a2: number`
- **Return Type**: `number`
### `getTforX(x: number): number`

<details><summary>Code</summary>

```ts
(x: number) => {
    let aGuessT = x

    for (let i = 0; i < 4; ++i) {
      const currentSlope = getSlope(aGuessT, p0, p2)
      if (currentSlope === 0)
        return aGuessT
      const currentX = calcBezier(aGuessT, p0, p2) - x
      aGuessT -= currentX / currentSlope
    }

    return aGuessT
  }
```
</details>

- **Parameters**:
  - `x: number`
- **Return Type**: `number`
- **Calls**:
  - `getSlope`
  - `calcBezier`
### `lerp(a: number, b: number, alpha: number): number`

<details><summary>Code</summary>

```ts
function lerp(a: number, b: number, alpha: number) {
  return a + alpha * (b - a)
}
```
</details>

- **Parameters**:
  - `a: number`
  - `b: number`
  - `alpha: number`
- **Return Type**: `number`
### `toVec(t: number | number[] | undefined): number[]`

<details><summary>Code</summary>

```ts
function toVec(t: number | number[] | undefined) {
  return (typeof t === 'number' ? [t] : t) || []
}
```
</details>

- **Parameters**:
  - `t: number | number[] | undefined`
- **Return Type**: `number[]`
### `executeTransition(source: Ref<T>, from: MaybeRefOrGetter<T>, to: MaybeRefOrGetter<T>, options: TransitionOptions): PromiseLike<void>`

<details><summary>Code</summary>

```ts
export function executeTransition<T extends number | number[]>(
  source: Ref<T>,
  from: MaybeRefOrGetter<T>,
  to: MaybeRefOrGetter<T>,
  options: TransitionOptions = {},
): PromiseLike<void> {
  const fromVal = toValue(from)
  const toVal = toValue(to)
  const v1 = toVec(fromVal)
  const v2 = toVec(toVal)
  const duration = toValue(options.duration) ?? 1000
  const startedAt = Date.now()
  const endAt = Date.now() + duration
  const trans = typeof options.transition === 'function'
    ? options.transition
    : (toValue(options.transition) ?? linear)

  const ease = typeof trans === 'function'
    ? trans
    : createEasingFunction(trans)

  return new Promise<void>((resolve) => {
    source.value = fromVal

    const tick = () => {
      if (options.abort?.()) {
        resolve()

        return
      }

      const now = Date.now()
      const alpha = ease((now - startedAt) / duration)
      const arr = toVec(source.value).map((n, i) => lerp(v1[i], v2[i], alpha))

      if (Array.isArray(source.value))
        (source.value as number[]) = arr.map((n, i) => lerp(v1[i] ?? 0, v2[i] ?? 0, alpha))
      else if (typeof source.value === 'number')
        (source.value as number) = arr[0]

      if (now < endAt) {
        requestAnimationFrame(tick)
      }
      else {
        source.value = toVal

        resolve()
      }
    }

    tick()
  })
}
```
</details>

- **JSDoc**:
```ts
/**
 * Transition from one value to another.
 *
 * @param source
 * @param from
 * @param to
 * @param options
 */
```

- **Parameters**:
  - `source: Ref<T>`
  - `from: MaybeRefOrGetter<T>`
  - `to: MaybeRefOrGetter<T>`
  - `options: TransitionOptions`
- **Return Type**: `PromiseLike<void>`
- **Calls**:
  - `toValue (from vue)`
  - `toVec`
  - `Date.now`
  - `createEasingFunction`
  - `options.abort`
  - `resolve`
  - `ease`
  - `toVec(source.value).map`
  - `lerp`
  - `Array.isArray`
  - `arr.map`
  - `requestAnimationFrame`
  - `tick`
### `tick(): void`

<details><summary>Code</summary>

```ts
() => {
      if (options.abort?.()) {
        resolve()

        return
      }

      const now = Date.now()
      const alpha = ease((now - startedAt) / duration)
      const arr = toVec(source.value).map((n, i) => lerp(v1[i], v2[i], alpha))

      if (Array.isArray(source.value))
        (source.value as number[]) = arr.map((n, i) => lerp(v1[i] ?? 0, v2[i] ?? 0, alpha))
      else if (typeof source.value === 'number')
        (source.value as number) = arr[0]

      if (now < endAt) {
        requestAnimationFrame(tick)
      }
      else {
        source.value = toVal

        resolve()
      }
    }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `options.abort`
  - `resolve`
  - `Date.now`
  - `ease`
  - `toVec(source.value).map`
  - `lerp`
  - `Array.isArray`
  - `arr.map`
  - `requestAnimationFrame`
### `useTransition(source: MaybeRefOrGetter<number>, options: UseTransitionOptions): ComputedRef<number>`

<details><summary>Code</summary>

```ts
export function useTransition(source: MaybeRefOrGetter<number>, options?: UseTransitionOptions): ComputedRef<number>
```
</details>

- **Parameters**:
  - `source: MaybeRefOrGetter<number>`
  - `options: UseTransitionOptions`
- **Return Type**: `ComputedRef<number>`
### `sourceVal(): any`

<details><summary>Code</summary>

```ts
() => {
    const v = toValue(source)

    return typeof v === 'number'
      ? v
      : v.map(toValue<number>)
  }
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `toValue (from vue)`
  - `v.map`
### `abort(): any`

<details><summary>Code</summary>

```ts
() => id !== currentId || options.abort?.()
```
</details>

- **Return Type**: `any`
### `abort(): any`

<details><summary>Code</summary>

```ts
() => id !== currentId || options.abort?.()
```
</details>

- **Return Type**: `any`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `TransitionOptions`

<details><summary>Interface Code</summary>

```ts
export interface TransitionOptions {

  /**
   * Manually abort a transition
   */
  abort?: () => any

  /**
   * Transition duration in milliseconds
   */
  duration?: MaybeRef<number>

  /**
   * Easing function or cubic bezier points for calculating transition values
   */
  transition?: MaybeRef<EasingFunction | CubicBezierPoints>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `abort` | `() => any` | ✓ |  |
| `duration` | `MaybeRef<number>` | ✓ |  |
| `transition` | `MaybeRef<EasingFunction | CubicBezierPoints>` | ✓ |  |

### `UseTransitionOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseTransitionOptions extends TransitionOptions {
  /**
   * Milliseconds to wait before starting transition
   */
  delay?: MaybeRef<number>

  /**
   * Disables the transition
   */
  disabled?: MaybeRef<boolean>

  /**
   * Callback to execute after transition finishes
   */
  onFinished?: () => void

  /**
   * Callback to execute after transition starts
   */
  onStarted?: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `delay` | `MaybeRef<number>` | ✓ |  |
| `disabled` | `MaybeRef<boolean>` | ✓ |  |
| `onFinished` | `() => void` | ✓ |  |
| `onStarted` | `() => void` | ✓ |  |


---

## Type Aliases

### `CubicBezierPoints`

/**
 * Cubic bezier points
 */

```ts
type CubicBezierPoints = [number, number, number, number];
```

### `EasingFunction`

/**
 * Easing function
 */

```ts
type EasingFunction = (n: number) => number;
```


---