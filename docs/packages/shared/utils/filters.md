[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `filters.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 14 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 14 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 5 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 5 |
| 📑 Type Aliases | 2 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/utils/filters.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `AnyFn` | `./types` |
| `ArgumentsType` | `./types` |
| `Awaited` | `./types` |
| `Pausable` | `./types` |
| `Promisify` | `./types` |
| `isRef` | `vue` |
| `readonly` | `vue` |
| `toValue` | `vue` |
| `toRef` | `../toRef` |
| `noop` | `./is` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `timer` | `ReturnType<typeof setTimeout> | undefined` | let/var | `*not shown*` | ✗ |
| `maxTimer` | `ReturnType<typeof setTimeout> | undefined | null` | let/var | `*not shown*` | ✗ |
| `lastRejector` | `AnyFn` | let/var | `noop` | ✗ |
| `lastInvoker` | `() => void` | let/var | `*not shown*` | ✗ |
| `lastExec` | `number` | let/var | `0` | ✗ |
| `timer` | `ReturnType<typeof setTimeout> | undefined` | let/var | `*not shown*` | ✗ |
| `isLeading` | `boolean` | let/var | `true` | ✗ |
| `lastRejector` | `AnyFn` | let/var | `noop` | ✗ |
| `lastValue` | `any` | let/var | `*not shown*` | ✗ |
| `ms` | `MaybeRefOrGetter<number>` | let/var | `*not shown*` | ✗ |
| `trailing` | `boolean` | let/var | `*not shown*` | ✗ |
| `leading` | `boolean` | let/var | `*not shown*` | ✗ |
| `rejectOnCancel` | `boolean` | let/var | `*not shown*` | ✗ |
| `elapsed` | `number` | const | `Date.now() - lastExec` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `createFilterWrapper` | *none* | new Promise(...), Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args }))
        .then(resolve).catch, Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args })).then, Promise.resolve |
| promise-chain | `wrapper` | *none* | new Promise(...), Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args }))
        .then(resolve).catch, Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args })).then, Promise.resolve |
| promise-chain | `debounceFilter` | *none* | Promise.resolve, new Promise(...) |
| promise-chain | `filter` | *none* | Promise.resolve, new Promise(...) |
| promise-chain | `filter` | *none* | new Promise(...) |


---

## Functions

### `createFilterWrapper(filter: EventFilter, fn: T): (this: any, ...args: ArgumentsType<T>) => Promise<Awaited<ReturnType<T>>>`

<details><summary>Code</summary>

```ts
export function createFilterWrapper<T extends AnyFn>(filter: EventFilter, fn: T) {
  function wrapper(this: any, ...args: ArgumentsType<T>) {
    return new Promise<Awaited<ReturnType<T>>>((resolve, reject) => {
      // make sure it's a promise
      Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args }))
        .then(resolve)
        .catch(reject)
    })
  }

  return wrapper
}
```
</details>

- **JSDoc**:
```ts
/**
 * @internal
 */
```

- **Parameters**:
  - `filter: EventFilter`
  - `fn: T`
- **Return Type**: `(this: any, ...args: ArgumentsType<T>) => Promise<Awaited<ReturnType<T>>>`
- **Calls**:
  - `Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args }))
        .then(resolve)
        .catch`
- **Internal Comments**:
```
// make sure it's a promise (x8)
```

### `wrapper(this: any, args: ArgumentsType<T>): Promise<Awaited<ReturnType<T>>>`

<details><summary>Code</summary>

```ts
function wrapper(this: any, ...args: ArgumentsType<T>) {
    return new Promise<Awaited<ReturnType<T>>>((resolve, reject) => {
      // make sure it's a promise
      Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args }))
        .then(resolve)
        .catch(reject)
    })
  }
```
</details>

- **Parameters**:
  - `this: any`
  - `args: ArgumentsType<T>`
- **Return Type**: `Promise<Awaited<ReturnType<T>>>`
- **Calls**:
  - `Promise.resolve(filter(() => fn.apply(this, args), { fn, thisArg: this, args }))
        .then(resolve)
        .catch`
- **Internal Comments**:
```
// make sure it's a promise (x8)
```

### `bypassFilter(invoke: AnyFn): any`

<details><summary>Code</summary>

```ts
(invoke) => {
  return invoke()
}
```
</details>

- **Parameters**:
  - `invoke: AnyFn`
- **Return Type**: `any`
- **Calls**:
  - `invoke`
### `debounceFilter(ms: MaybeRefOrGetter<number>, options: DebounceFilterOptions): EventFilter<any[], any, AnyFn>`

<details><summary>Code</summary>

```ts
export function debounceFilter(ms: MaybeRefOrGetter<number>, options: DebounceFilterOptions = {}) {
  let timer: ReturnType<typeof setTimeout> | undefined
  let maxTimer: ReturnType<typeof setTimeout> | undefined | null
  let lastRejector: AnyFn = noop

  const _clearTimeout = (timer: ReturnType<typeof setTimeout>) => {
    clearTimeout(timer)
    lastRejector()
    lastRejector = noop
  }

  let lastInvoker: () => void

  const filter: EventFilter = (invoke) => {
    const duration = toValue(ms)
    const maxDuration = toValue(options.maxWait)

    if (timer)
      _clearTimeout(timer)

    if (duration <= 0 || (maxDuration !== undefined && maxDuration <= 0)) {
      if (maxTimer) {
        _clearTimeout(maxTimer)
        maxTimer = null
      }
      return Promise.resolve(invoke())
    }

    return new Promise((resolve, reject) => {
      lastRejector = options.rejectOnCancel ? reject : resolve
      lastInvoker = invoke
      // Create the maxTimer. Clears the regular timer on invoke
      if (maxDuration && !maxTimer) {
        maxTimer = setTimeout(() => {
          if (timer)
            _clearTimeout(timer)
          maxTimer = null
          resolve(lastInvoker())
        }, maxDuration)
      }

      // Create the regular timer. Clears the max timer on invoke
      timer = setTimeout(() => {
        if (maxTimer)
          _clearTimeout(maxTimer)
        maxTimer = null
        resolve(invoke())
      }, duration)
    })
  }

  return filter
}
```
</details>

- **JSDoc**:
```ts
/**
 * Create an EventFilter that debounce the events
 */
```

- **Parameters**:
  - `ms: MaybeRefOrGetter<number>`
  - `options: DebounceFilterOptions`
- **Return Type**: `EventFilter<any[], any, AnyFn>`
- **Calls**:
  - `clearTimeout`
  - `lastRejector`
  - `toValue (from vue)`
  - `_clearTimeout`
  - `Promise.resolve`
  - `invoke`
  - `setTimeout`
  - `resolve`
  - `lastInvoker`
- **Internal Comments**:
```
// Create the maxTimer. Clears the regular timer on invoke
// Create the regular timer. Clears the max timer on invoke (x3)
```

### `_clearTimeout(timer: ReturnType<typeof setTimeout>): void`

<details><summary>Code</summary>

```ts
(timer: ReturnType<typeof setTimeout>) => {
    clearTimeout(timer)
    lastRejector()
    lastRejector = noop
  }
```
</details>

- **Parameters**:
  - `timer: ReturnType<typeof setTimeout>`
- **Return Type**: `void`
- **Calls**:
  - `clearTimeout`
  - `lastRejector`
### `filter(invoke: AnyFn): Promise<any>`

<details><summary>Code</summary>

```ts
(invoke) => {
    const duration = toValue(ms)
    const maxDuration = toValue(options.maxWait)

    if (timer)
      _clearTimeout(timer)

    if (duration <= 0 || (maxDuration !== undefined && maxDuration <= 0)) {
      if (maxTimer) {
        _clearTimeout(maxTimer)
        maxTimer = null
      }
      return Promise.resolve(invoke())
    }

    return new Promise((resolve, reject) => {
      lastRejector = options.rejectOnCancel ? reject : resolve
      lastInvoker = invoke
      // Create the maxTimer. Clears the regular timer on invoke
      if (maxDuration && !maxTimer) {
        maxTimer = setTimeout(() => {
          if (timer)
            _clearTimeout(timer)
          maxTimer = null
          resolve(lastInvoker())
        }, maxDuration)
      }

      // Create the regular timer. Clears the max timer on invoke
      timer = setTimeout(() => {
        if (maxTimer)
          _clearTimeout(maxTimer)
        maxTimer = null
        resolve(invoke())
      }, duration)
    })
  }
```
</details>

- **Parameters**:
  - `invoke: AnyFn`
- **Return Type**: `Promise<any>`
- **Calls**:
  - `toValue (from vue)`
  - `_clearTimeout`
  - `Promise.resolve`
  - `invoke`
  - `setTimeout`
  - `resolve`
  - `lastInvoker`
- **Internal Comments**:
```
// Create the maxTimer. Clears the regular timer on invoke
// Create the regular timer. Clears the max timer on invoke (x3)
```

### `throttleFilter(ms: MaybeRefOrGetter<number>, trailing: boolean, leading: boolean, rejectOnCancel: boolean): EventFilter`

<details><summary>Code</summary>

```ts
export function throttleFilter(ms: MaybeRefOrGetter<number>, trailing?: boolean, leading?: boolean, rejectOnCancel?: boolean): EventFilter
```
</details>

- **JSDoc**:
```ts
/**
 * Create an EventFilter that throttle the events
 *
 * @param ms
 * @param [trailing]
 * @param [leading]
 * @param [rejectOnCancel]
 */
```

- **Parameters**:
  - `ms: MaybeRefOrGetter<number>`
  - `trailing: boolean`
  - `leading: boolean`
  - `rejectOnCancel: boolean`
- **Return Type**: `EventFilter`
### `clear(): void`

<details><summary>Code</summary>

```ts
() => {
    if (timer) {
      clearTimeout(timer)
      timer = undefined
      lastRejector()
      lastRejector = noop
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `clearTimeout`
  - `lastRejector`
### `filter(_invoke: AnyFn): any`

<details><summary>Code</summary>

```ts
(_invoke) => {
    const duration = toValue(ms)
    const elapsed = Date.now() - lastExec
    const invoke = () => {
      return lastValue = _invoke()
    }

    clear()

    if (duration <= 0) {
      lastExec = Date.now()
      return invoke()
    }

    if (elapsed > duration && (leading || !isLeading)) {
      lastExec = Date.now()
      invoke()
    }
    else if (trailing) {
      lastValue = new Promise((resolve, reject) => {
        lastRejector = rejectOnCancel ? reject : resolve
        timer = setTimeout(() => {
          lastExec = Date.now()
          isLeading = true
          resolve(invoke())
          clear()
        }, Math.max(0, duration - elapsed))
      })
    }

    if (!leading && !timer)
      timer = setTimeout(() => isLeading = true, duration)

    isLeading = false
    return lastValue
  }
```
</details>

- **Parameters**:
  - `_invoke: AnyFn`
- **Return Type**: `any`
- **Calls**:
  - `toValue (from vue)`
  - `Date.now`
  - `_invoke`
  - `clear`
  - `invoke`
  - `setTimeout`
  - `resolve`
  - `Math.max`
### `invoke(): any`

<details><summary>Code</summary>

```ts
() => {
      return lastValue = _invoke()
    }
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `_invoke`
### `pausableFilter(extendFilter: EventFilter, options: PausableFilterOptions): Pausable & { eventFilter: EventFilter }`

<details><summary>Code</summary>

```ts
export function pausableFilter(extendFilter: EventFilter = bypassFilter, options: PausableFilterOptions = {}): Pausable & { eventFilter: EventFilter } {
  const {
    initialState = 'active',
  } = options

  const isActive = toRef(initialState === 'active')

  function pause() {
    isActive.value = false
  }
  function resume() {
    isActive.value = true
  }

  const eventFilter: EventFilter = (...args) => {
    if (isActive.value)
      extendFilter(...args)
  }

  return { isActive: readonly(isActive), pause, resume, eventFilter }
}
```
</details>

- **JSDoc**:
```ts
/**
 * EventFilter that gives extra controls to pause and resume the filter
 *
 * @param extendFilter  Extra filter to apply when the PausableFilter is active, default to none
 * @param options Options to configure the filter
 */
```

- **Parameters**:
  - `extendFilter: EventFilter`
  - `options: PausableFilterOptions`
- **Return Type**: `Pausable & { eventFilter: EventFilter }`
- **Calls**:
  - `toRef (from ../toRef)`
  - `extendFilter`
  - `readonly (from vue)`
### `pause(): void`

<details><summary>Code</summary>

```ts
function pause() {
    isActive.value = false
  }
```
</details>

- **Return Type**: `void`
### `resume(): void`

<details><summary>Code</summary>

```ts
function resume() {
    isActive.value = true
  }
```
</details>

- **Return Type**: `void`
### `eventFilter(args: [invoke: AnyFn, options: FunctionWrapperOptions<any[], any>]): void`

<details><summary>Code</summary>

```ts
(...args) => {
    if (isActive.value)
      extendFilter(...args)
  }
```
</details>

- **Parameters**:
  - `args: [invoke: AnyFn, options: FunctionWrapperOptions<any[], any>]`
- **Return Type**: `void`
- **Calls**:
  - `extendFilter`

---

## Interfaces

### `FunctionWrapperOptions<Args extends any[] = any[], This = any>`

<details><summary>Interface Code</summary>

```ts
export interface FunctionWrapperOptions<Args extends any[] = any[], This = any> {
  fn: FunctionArgs<Args, This>
  args: Args
  thisArg: This
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `fn` | `FunctionArgs<Args, This>` | ✗ |  |
| `args` | `Args` | ✗ |  |
| `thisArg` | `This` | ✗ |  |

### `ConfigurableEventFilter`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableEventFilter {
  /**
   * Filter for if events should to be received.
   *
   * @see https://vueuse.org/guide/config.html#event-filters
   */
  eventFilter?: EventFilter
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `eventFilter` | `EventFilter` | ✓ |  |

### `DebounceFilterOptions`

<details><summary>Interface Code</summary>

```ts
export interface DebounceFilterOptions {
  /**
   * The maximum time allowed to be delayed before it's invoked.
   * In milliseconds.
   */
  maxWait?: MaybeRefOrGetter<number>

  /**
   * Whether to reject the last call if it's been cancel.
   *
   * @default false
   */
  rejectOnCancel?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `maxWait` | `MaybeRefOrGetter<number>` | ✓ |  |
| `rejectOnCancel` | `boolean` | ✓ |  |

### `ThrottleFilterOptions`

<details><summary>Interface Code</summary>

```ts
export interface ThrottleFilterOptions {
  /**
   * The maximum time allowed to be delayed before it's invoked.
   */
  delay: MaybeRefOrGetter<number>
  /**
   * Whether to invoke on the trailing edge of the timeout.
   */
  trailing?: boolean
  /**
   * Whether to invoke on the leading edge of the timeout.
   */
  leading?: boolean
  /**
   * Whether to reject the last call if it's been cancel.
   */
  rejectOnCancel?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `delay` | `MaybeRefOrGetter<number>` | ✗ |  |
| `trailing` | `boolean` | ✓ |  |
| `leading` | `boolean` | ✓ |  |
| `rejectOnCancel` | `boolean` | ✓ |  |

### `PausableFilterOptions`

<details><summary>Interface Code</summary>

```ts
export interface PausableFilterOptions {
  /**
   * The initial state
   *
   * @default 'active'
   */
  initialState?: 'active' | 'paused'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialState` | `'active' | 'paused'` | ✓ |  |


---

## Type Aliases

### `FunctionArgs<Args extends any[] = any[] extends any[] = any[], Return = void = void>`

```ts
type FunctionArgs<Args extends any[] = any[] extends any[] = any[], Return = void = void> = (...args: Args) => Return;
```

### `EventFilter<Args extends any[] = any[] extends any[] = any[], This = any = any, Invoke extends AnyFn = AnyFn extends AnyFn = AnyFn>`

```ts
type EventFilter<Args extends any[] = any[] extends any[] = any[], This = any = any, Invoke extends AnyFn = AnyFn extends AnyFn = AnyFn> = (
  invoke: Invoke,
  options: FunctionWrapperOptions<Args, This>
) => ReturnType<Invoke> | Promisify<ReturnType<Invoke>>;
```


---