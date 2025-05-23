[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 1
- **Type Aliases**: 0

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

## Classes

> No classes found in this file.


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

## Type Aliases

> No type aliases found in this file.


---