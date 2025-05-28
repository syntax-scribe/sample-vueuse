[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 9 |
| 🧱 Classes | 0 |
| 📦 Imports | 21 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 9 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 3 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useAnimate/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Mutable` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `ShallowRef` | `vue` |
| `WritableComputedRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeComputedElementRef` | `../unrefElement` |
| `isObject` | `@vueuse/shared` |
| `objectOmit` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowReactive` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |
| `useRafFn` | `../useRafFn` |
| `useSupported` | `../useSupported` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `config` | `UseAnimateOptions` | let/var | `*not shown*` | ✗ |
| `animateOptions` | `undefined | number | KeyframeAnimationOptions` | let/var | `*not shown*` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `useAnimate(target: MaybeComputedElementRef, keyframes: UseAnimateKeyframes, options: number | UseAnimateOptions): UseAnimateReturn`

<details><summary>Code</summary>

```ts
export function useAnimate(
  target: MaybeComputedElementRef,
  keyframes: UseAnimateKeyframes,
  options?: number | UseAnimateOptions,
): UseAnimateReturn {
  let config: UseAnimateOptions
  let animateOptions: undefined | number | KeyframeAnimationOptions

  if (isObject(options)) {
    config = options
    animateOptions = objectOmit(options, ['window', 'immediate', 'commitStyles', 'persist', 'onReady', 'onError'])
  }
  else {
    config = { duration: options }
    animateOptions = options
  }

  const {
    window = defaultWindow,
    immediate = true,
    commitStyles,
    persist,
    playbackRate: _playbackRate = 1,
    onReady,
    onError = (e: unknown) => {
      console.error(e)
    },
  } = config

  const isSupported = useSupported(() => window && HTMLElement && 'animate' in HTMLElement.prototype)

  const animate = shallowRef<Animation | undefined>(undefined)
  const store = shallowReactive<AnimateStore>({
    startTime: null,
    currentTime: null,
    timeline: null,
    playbackRate: _playbackRate,
    pending: false,
    playState: immediate ? 'idle' : 'paused',
    replaceState: 'active',
  })

  const pending = computed(() => store.pending)
  const playState = computed(() => store.playState)
  const replaceState = computed(() => store.replaceState)

  const startTime = computed<CSSNumberish | number | null>({
    get() {
      return store.startTime
    },
    set(value) {
      store.startTime = value
      if (animate.value)
        animate.value.startTime = value
    },
  })

  const currentTime = computed({
    get() {
      return store.currentTime
    },
    set(value) {
      store.currentTime = value
      if (animate.value) {
        animate.value.currentTime = value
        syncResume()
      }
    },
  })

  const timeline = computed({
    get() {
      return store.timeline
    },
    set(value) {
      store.timeline = value
      if (animate.value)
        animate.value.timeline = value
    },
  })

  const playbackRate = computed({
    get() {
      return store.playbackRate
    },
    set(value) {
      store.playbackRate = value
      if (animate.value)
        animate.value.playbackRate = value
    },
  })

  const play = () => {
    if (animate.value) {
      try {
        animate.value.play()
        syncResume()
      }
      catch (e) {
        syncPause()
        onError(e)
      }
    }
    else {
      update()
    }
  }

  const pause = () => {
    try {
      animate.value?.pause()
      syncPause()
    }
    catch (e) {
      onError(e)
    }
  }

  const reverse = () => {
    if (!animate.value)
      update()
    try {
      animate.value?.reverse()
      syncResume()
    }
    catch (e) {
      syncPause()
      onError(e)
    }
  }

  const finish = () => {
    try {
      animate.value?.finish()
      syncPause()
    }
    catch (e) {
      onError(e)
    }
  }

  const cancel = () => {
    try {
      animate.value?.cancel()
      syncPause()
    }
    catch (e) {
      onError(e)
    }
  }

  watch(() => unrefElement(target), (el) => {
    if (el) {
      update()
    }
    else {
      animate.value = undefined
    }
  })

  watch(() => keyframes, (value) => {
    if (animate.value) {
      update()

      const targetEl = unrefElement(target)
      if (targetEl) {
        animate.value.effect = new KeyframeEffect(
          targetEl,
          toValue(value),
          animateOptions,
        )
      }
    }
  }, { deep: true })

  tryOnMounted(() => update(true), false)

  tryOnScopeDispose(cancel)

  function update(init?: boolean) {
    const el = unrefElement(target)
    if (!isSupported.value || !el)
      return

    if (!animate.value)
      animate.value = el.animate(toValue(keyframes), animateOptions)

    if (persist)
      animate.value.persist()
    if (_playbackRate !== 1)
      animate.value.playbackRate = _playbackRate

    if (init && !immediate)
      animate.value.pause()
    else
      syncResume()

    onReady?.(animate.value)
  }

  const listenerOptions = { passive: true }
  useEventListener(animate, ['cancel', 'finish', 'remove'], syncPause, listenerOptions)
  useEventListener(animate, 'finish', () => {
    if (commitStyles)
      animate.value?.commitStyles()
  }, listenerOptions)

  const { resume: resumeRef, pause: pauseRef } = useRafFn(() => {
    if (!animate.value)
      return
    store.pending = animate.value.pending
    store.playState = animate.value.playState
    store.replaceState = animate.value.replaceState
    store.startTime = animate.value.startTime
    store.currentTime = animate.value.currentTime
    store.timeline = animate.value.timeline
    store.playbackRate = animate.value.playbackRate
  }, { immediate: false })

  function syncResume() {
    if (isSupported.value)
      resumeRef()
  }

  function syncPause() {
    if (isSupported.value && window)
      window.requestAnimationFrame(pauseRef)
  }

  return {
    isSupported,
    animate,

    // actions
    play,
    pause,
    reverse,
    finish,
    cancel,

    // state
    pending,
    playState,
    replaceState,
    startTime,
    currentTime,
    timeline,
    playbackRate,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Web Animations API
 *
 * @see https://vueuse.org/useAnimate
 * @param target
 * @param keyframes
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeComputedElementRef`
  - `keyframes: UseAnimateKeyframes`
  - `options: number | UseAnimateOptions`
- **Return Type**: `UseAnimateReturn`
- **Calls**:
  - `isObject (from @vueuse/shared)`
  - `objectOmit (from @vueuse/shared)`
  - `console.error`
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `shallowReactive (from vue)`
  - `computed (from vue)`
  - `syncResume`
  - `animate.value.play`
  - `syncPause`
  - `onError`
  - `update`
  - `animate.value?.pause`
  - `animate.value?.reverse`
  - `animate.value?.finish`
  - `animate.value?.cancel`
  - `watch (from vue)`
  - `unrefElement (from ../unrefElement)`
  - `toValue (from vue)`
  - `tryOnMounted (from @vueuse/shared)`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `el.animate`
  - `animate.value.persist`
  - `animate.value.pause`
  - `onReady`
  - `useEventListener (from ../useEventListener)`
  - `animate.value?.commitStyles`
  - `useRafFn (from ../useRafFn)`
  - `resumeRef`
  - `window.requestAnimationFrame`
- **Internal Comments**:
```
// actions (x2)
// state (x2)
```

### `play(): void`

<details><summary>Code</summary>

```ts
() => {
    if (animate.value) {
      try {
        animate.value.play()
        syncResume()
      }
      catch (e) {
        syncPause()
        onError(e)
      }
    }
    else {
      update()
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `animate.value.play`
  - `syncResume`
  - `syncPause`
  - `onError`
  - `update`
### `pause(): void`

<details><summary>Code</summary>

```ts
() => {
    try {
      animate.value?.pause()
      syncPause()
    }
    catch (e) {
      onError(e)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `animate.value?.pause`
  - `syncPause`
  - `onError`
### `reverse(): void`

<details><summary>Code</summary>

```ts
() => {
    if (!animate.value)
      update()
    try {
      animate.value?.reverse()
      syncResume()
    }
    catch (e) {
      syncPause()
      onError(e)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `update`
  - `animate.value?.reverse`
  - `syncResume`
  - `syncPause`
  - `onError`
### `finish(): void`

<details><summary>Code</summary>

```ts
() => {
    try {
      animate.value?.finish()
      syncPause()
    }
    catch (e) {
      onError(e)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `animate.value?.finish`
  - `syncPause`
  - `onError`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => {
    try {
      animate.value?.cancel()
      syncPause()
    }
    catch (e) {
      onError(e)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `animate.value?.cancel`
  - `syncPause`
  - `onError`
### `update(init: boolean): void`

<details><summary>Code</summary>

```ts
function update(init?: boolean) {
    const el = unrefElement(target)
    if (!isSupported.value || !el)
      return

    if (!animate.value)
      animate.value = el.animate(toValue(keyframes), animateOptions)

    if (persist)
      animate.value.persist()
    if (_playbackRate !== 1)
      animate.value.playbackRate = _playbackRate

    if (init && !immediate)
      animate.value.pause()
    else
      syncResume()

    onReady?.(animate.value)
  }
```
</details>

- **Parameters**:
  - `init: boolean`
- **Return Type**: `void`
- **Calls**:
  - `unrefElement (from ../unrefElement)`
  - `el.animate`
  - `toValue (from vue)`
  - `animate.value.persist`
  - `animate.value.pause`
  - `syncResume`
  - `onReady`
### `syncResume(): void`

<details><summary>Code</summary>

```ts
function syncResume() {
    if (isSupported.value)
      resumeRef()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `resumeRef`
### `syncPause(): void`

<details><summary>Code</summary>

```ts
function syncPause() {
    if (isSupported.value && window)
      window.requestAnimationFrame(pauseRef)
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `window.requestAnimationFrame`

---

## Interfaces

### `UseAnimateOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseAnimateOptions extends KeyframeAnimationOptions, ConfigurableWindow {
  /**
   * Will automatically run play when `useAnimate` is used
   *
   * @default true
   */
  immediate?: boolean
  /**
   * Whether to commits the end styling state of an animation to the element being animated
   * In general, you should use `fill` option with this.
   *
   * @default false
   */
  commitStyles?: boolean
  /**
   * Whether to persists the animation
   *
   * @default false
   */
  persist?: boolean
  /**
   * Executed after animation initialization
   */
  onReady?: (animate: Animation) => void
  /**
   * Callback when error is caught.
   */
  onError?: (e: unknown) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |
| `commitStyles` | `boolean` | ✓ |  |
| `persist` | `boolean` | ✓ |  |
| `onReady` | `(animate: Animation) => void` | ✓ |  |
| `onError` | `(e: unknown) => void` | ✓ |  |

### `UseAnimateReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseAnimateReturn {
  isSupported: ComputedRef<boolean>
  animate: ShallowRef<Animation | undefined>
  play: () => void
  pause: () => void
  reverse: () => void
  finish: () => void
  cancel: () => void

  pending: ComputedRef<boolean>
  playState: ComputedRef<AnimationPlayState>
  replaceState: ComputedRef<AnimationReplaceState>
  startTime: WritableComputedRef<CSSNumberish | number | null>
  currentTime: WritableComputedRef<CSSNumberish | null>
  timeline: WritableComputedRef<AnimationTimeline | null>
  playbackRate: WritableComputedRef<number>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `animate` | `ShallowRef<Animation | undefined>` | ✗ |  |
| `play` | `() => void` | ✗ |  |
| `pause` | `() => void` | ✗ |  |
| `reverse` | `() => void` | ✗ |  |
| `finish` | `() => void` | ✗ |  |
| `cancel` | `() => void` | ✗ |  |
| `pending` | `ComputedRef<boolean>` | ✗ |  |
| `playState` | `ComputedRef<AnimationPlayState>` | ✗ |  |
| `replaceState` | `ComputedRef<AnimationReplaceState>` | ✗ |  |
| `startTime` | `WritableComputedRef<CSSNumberish | number | null>` | ✗ |  |
| `currentTime` | `WritableComputedRef<CSSNumberish | null>` | ✗ |  |
| `timeline` | `WritableComputedRef<AnimationTimeline | null>` | ✗ |  |
| `playbackRate` | `WritableComputedRef<number>` | ✗ |  |


---

## Type Aliases

### `UseAnimateKeyframes`

```ts
type UseAnimateKeyframes = MaybeRef<Keyframe[] | PropertyIndexedKeyframes | null>;
```

### `AnimateStoreKeys`

```ts
type AnimateStoreKeys = Extract<keyof Animation, 'startTime' | 'currentTime' | 'timeline' | 'playbackRate' | 'pending' | 'playState' | 'replaceState'>;
```

### `AnimateStore`

```ts
type AnimateStore = Mutable<Pick<Animation, AnimateStoreKeys>>;
```


---