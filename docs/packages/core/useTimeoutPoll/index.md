[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 8 |
| ⚡ Async/Await Patterns | 2 |
| 📐 Interfaces | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useTimeoutPoll/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Awaitable` | `@vueuse/shared` |
| `Pausable` | `@vueuse/shared` |
| `UseTimeoutFnOptions` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `isClient` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `useTimeoutFn` | `@vueuse/shared` |
| `shallowRef` | `vue` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useTimeoutPoll` | fn() | *none* |
| async-function | `loop` | fn() | *none* |


---

## Functions

### `useTimeoutPoll(fn: () => Awaitable<void>, interval: MaybeRefOrGetter<number>, options: UseTimeoutFnOptions): Pausable`

<details><summary>Code</summary>

```ts
export function useTimeoutPoll(
  fn: () => Awaitable<void>,
  interval: MaybeRefOrGetter<number>,
  options: UseTimeoutFnOptions = {},
): Pausable {
  const {
    immediate = true,
    immediateCallback = false,
  } = options

  const { start } = useTimeoutFn(loop, interval, { immediate })

  const isActive = shallowRef(false)

  async function loop() {
    if (!isActive.value)
      return

    await fn()
    start()
  }

  function resume() {
    if (!isActive.value) {
      isActive.value = true
      if (immediateCallback)
        fn()
      start()
    }
  }

  function pause() {
    isActive.value = false
  }

  if (immediate && isClient)
    resume()

  tryOnScopeDispose(pause)

  return {
    isActive,
    pause,
    resume,
  }
}
```
</details>

- **Parameters**:
  - `fn: () => Awaitable<void>`
  - `interval: MaybeRefOrGetter<number>`
  - `options: UseTimeoutFnOptions`
- **Return Type**: `Pausable`
- **Calls**:
  - `useTimeoutFn (from @vueuse/shared)`
  - `shallowRef (from vue)`
  - `fn`
  - `start`
  - `resume`
  - `tryOnScopeDispose (from @vueuse/shared)`
### `loop(): Promise<void>`

<details><summary>Code</summary>

```ts
async function loop() {
    if (!isActive.value)
      return

    await fn()
    start()
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `fn`
  - `start`
### `resume(): void`

<details><summary>Code</summary>

```ts
function resume() {
    if (!isActive.value) {
      isActive.value = true
      if (immediateCallback)
        fn()
      start()
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `fn`
  - `start`
### `pause(): void`

<details><summary>Code</summary>

```ts
function pause() {
    isActive.value = false
  }
```
</details>

- **Return Type**: `void`

---

## Interfaces

### `UseTimeoutPollOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseTimeoutPollOptions {
  /**
   * Start the timer immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Execute the callback immediately after calling `resume`
   *
   * @default false
   */
  immediateCallback?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `immediate` | `boolean` | ✓ |  |
| `immediateCallback` | `boolean` | ✓ |  |


---