[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 5
- **Classes**: 0
- **Imports**: 18
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/integrations/useFocusTrap/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Arrayable` | `@vueuse/core` |
| `Fn` | `@vueuse/core` |
| `MaybeComputedElementRef` | `@vueuse/core` |
| `ActivateOptions` | `focus-trap` |
| `DeactivateOptions` | `focus-trap` |
| `FocusTrap` | `focus-trap` |
| `Options` | `focus-trap` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `toArray` | `@vueuse/core` |
| `tryOnScopeDispose` | `@vueuse/core` |
| `unrefElement` | `@vueuse/core` |
| `notNullish` | `@vueuse/shared` |
| `createFocusTrap` | `focus-trap` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useFocusTrap(target: Arrayable<MaybeRefOrGetter<string> | MaybeComputedElementRef>, options: UseFocusTrapOptions): UseFocusTrapReturn`

<details><summary>Code</summary>

```ts
export function useFocusTrap(
  target: Arrayable<MaybeRefOrGetter<string> | MaybeComputedElementRef>,
  options: UseFocusTrapOptions = {},
): UseFocusTrapReturn {
  let trap: undefined | FocusTrap

  const { immediate, ...focusTrapOptions } = options
  const hasFocus = shallowRef(false)
  const isPaused = shallowRef(false)

  const activate = (opts?: ActivateOptions) => trap && trap.activate(opts)
  const deactivate = (opts?: DeactivateOptions) => trap && trap.deactivate(opts)

  const pause = () => {
    if (trap) {
      trap.pause()
      isPaused.value = true
    }
  }

  const unpause = () => {
    if (trap) {
      trap.unpause()
      isPaused.value = false
    }
  }

  const targets = computed(() => {
    const _targets = toValue(target)
    return toArray(_targets)
      .map((el) => {
        const _el = toValue(el)
        return typeof _el === 'string' ? _el : unrefElement(_el)
      })
      .filter(notNullish)
  })

  watch(
    targets,
    (els) => {
      if (!els.length)
        return

      trap = createFocusTrap(els, {
        ...focusTrapOptions,
        onActivate() {
          hasFocus.value = true

          // Apply if user provided onActivate option
          if (options.onActivate)
            options.onActivate()
        },
        onDeactivate() {
          hasFocus.value = false

          // Apply if user provided onDeactivate option
          if (options.onDeactivate)
            options.onDeactivate()
        },
      })

      // Focus if immediate is set to true
      if (immediate)
        activate()
    },
    { flush: 'post' },
  )

  // Cleanup on unmount
  tryOnScopeDispose(() => deactivate())

  return {
    hasFocus,
    isPaused,
    activate,
    deactivate,
    pause,
    unpause,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive focus-trap
 *
 * @see https://vueuse.org/useFocusTrap
 */
```

- **Parameters**:
  - `target: Arrayable<MaybeRefOrGetter<string> | MaybeComputedElementRef>`
  - `options: UseFocusTrapOptions`
- **Return Type**: `UseFocusTrapReturn`
- **Calls**:
  - `shallowRef (from vue)`
  - `trap.activate`
  - `trap.deactivate`
  - `trap.pause`
  - `trap.unpause`
  - `computed (from vue)`
  - `toValue (from vue)`
  - `toArray(_targets)
      .map((el) => {
        const _el = toValue(el)
        return typeof _el === 'string' ? _el : unrefElement(_el)
      })
      .filter`
  - `watch (from vue)`
  - `createFocusTrap (from focus-trap)`
  - `options.onActivate`
  - `options.onDeactivate`
  - `activate`
  - `tryOnScopeDispose (from @vueuse/core)`
  - `deactivate`
- **Internal Comments**:
```
// Apply if user provided onActivate option
// Apply if user provided onDeactivate option
// Focus if immediate is set to true
// Cleanup on unmount (x3)
```

### `activate(opts: ActivateOptions): any`

<details><summary>Code</summary>

```ts
(opts?: ActivateOptions) => trap && trap.activate(opts)
```
</details>

- **Parameters**:
  - `opts: ActivateOptions`
- **Return Type**: `any`
### `deactivate(opts: DeactivateOptions): any`

<details><summary>Code</summary>

```ts
(opts?: DeactivateOptions) => trap && trap.deactivate(opts)
```
</details>

- **Parameters**:
  - `opts: DeactivateOptions`
- **Return Type**: `any`
### `pause(): void`

<details><summary>Code</summary>

```ts
() => {
    if (trap) {
      trap.pause()
      isPaused.value = true
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `trap.pause`
### `unpause(): void`

<details><summary>Code</summary>

```ts
() => {
    if (trap) {
      trap.unpause()
      isPaused.value = false
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `trap.unpause`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseFocusTrapOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFocusTrapOptions extends Options {
  /**
   * Immediately activate the trap
   */
  immediate?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |

### `UseFocusTrapReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseFocusTrapReturn {
  /**
   * Indicates if the focus trap is currently active
   */
  hasFocus: ShallowRef<boolean>

  /**
   * Indicates if the focus trap is currently paused
   */
  isPaused: ShallowRef<boolean>

  /**
   * Activate the focus trap
   *
   * @see https://github.com/focus-trap/focus-trap#trapactivateactivateoptions
   * @param opts Activate focus trap options
   */
  activate: (opts?: ActivateOptions) => void

  /**
   * Deactivate the focus trap
   *
   * @see https://github.com/focus-trap/focus-trap#trapdeactivatedeactivateoptions
   * @param opts Deactivate focus trap options
   */
  deactivate: (opts?: DeactivateOptions) => void

  /**
   * Pause the focus trap
   *
   * @see https://github.com/focus-trap/focus-trap#trappause
   */
  pause: Fn

  /**
   * Unpauses the focus trap
   *
   * @see https://github.com/focus-trap/focus-trap#trapunpause
   */
  unpause: Fn
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `hasFocus` | `ShallowRef<boolean>` | ✗ |  |
| `isPaused` | `ShallowRef<boolean>` | ✗ |  |
| `activate` | `(opts?: ActivateOptions) => void` | ✗ |  |
| `deactivate` | `(opts?: DeactivateOptions) => void` | ✗ |  |
| `pause` | `Fn` | ✗ |  |
| `unpause` | `Fn` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---