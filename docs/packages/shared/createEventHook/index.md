[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 2
- **Interfaces**: 1
- **Type Aliases**: 5

## 🛠️ File Location:
📂 **`packages/shared/createEventHook/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IsAny` | `../utils/types` |
| `tryOnScopeDispose` | `../tryOnScopeDispose` |


---

## Functions

### `createEventHook(): EventHookReturn<T>`

<details><summary>Code</summary>

```ts
export function createEventHook<T = any>(): EventHookReturn<T> {
  const fns: Set<Callback<T>> = new Set()

  const off = (fn: Callback<T>) => {
    fns.delete(fn)
  }

  const clear = () => {
    fns.clear()
  }

  const on = (fn: Callback<T>) => {
    fns.add(fn)
    const offFn = () => off(fn)

    tryOnScopeDispose(offFn)

    return {
      off: offFn,
    }
  }

  const trigger: EventHookTrigger<T> = (...args) => {
    return Promise.all(Array.from(fns).map(fn => fn(...args)))
  }

  return {
    on,
    off,
    trigger,
    clear,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Utility for creating event hooks
 *
 * @see https://vueuse.org/createEventHook
 */
```

- **Return Type**: `EventHookReturn<T>`
- **Calls**:
  - `fns.delete`
  - `fns.clear`
  - `fns.add`
  - `off`
  - `tryOnScopeDispose (from ../tryOnScopeDispose)`
  - `Promise.all`
  - `Array.from(fns).map`
  - `fn`
### `off(fn: Callback<T>): void`

<details><summary>Code</summary>

```ts
(fn: Callback<T>) => {
    fns.delete(fn)
  }
```
</details>

- **Parameters**:
  - `fn: Callback<T>`
- **Return Type**: `void`
- **Calls**:
  - `fns.delete`
### `clear(): void`

<details><summary>Code</summary>

```ts
() => {
    fns.clear()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `fns.clear`
### `on(fn: Callback<T>): { off: () => void; }`

<details><summary>Code</summary>

```ts
(fn: Callback<T>) => {
    fns.add(fn)
    const offFn = () => off(fn)

    tryOnScopeDispose(offFn)

    return {
      off: offFn,
    }
  }
```
</details>

- **Parameters**:
  - `fn: Callback<T>`
- **Return Type**: `{ off: () => void; }`
- **Calls**:
  - `fns.add`
  - `off`
  - `tryOnScopeDispose (from ../tryOnScopeDispose)`
### `offFn(): void`

<details><summary>Code</summary>

```ts
() => off(fn)
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `off`
### `trigger(args: Parameters<Callback<T>>): Promise<void[]>`

<details><summary>Code</summary>

```ts
(...args) => {
    return Promise.all(Array.from(fns).map(fn => fn(...args)))
  }
```
</details>

- **Parameters**:
  - `args: Parameters<Callback<T>>`
- **Return Type**: `Promise<void[]>`
- **Calls**:
  - `Promise.all`
  - `Array.from(fns).map`
  - `fn`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `EventHook<T = any>`

<details><summary>Interface Code</summary>

```ts
export interface EventHook<T = any> {
  on: EventHookOn<T>
  off: EventHookOff<T>
  trigger: EventHookTrigger<T>
  clear: () => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `on` | `EventHookOn<T>` | ✗ |  |
| `off` | `EventHookOff<T>` | ✗ |  |
| `trigger` | `EventHookTrigger<T>` | ✗ |  |
| `clear` | `() => void` | ✗ |  |


---

## Type Aliases

### `Callback<T>`

```ts
type Callback<T> = IsAny<T> extends true
  ? (...param: any) => void
  : (
      [T] extends [void]
        ? (...param: unknown[]) => void
        : [T] extends [any[]]
            ? (...param: T) => void
            : (...param: [T, ...unknown[]]) => void
    );
```

### `EventHookOn<T = any = any>`

```ts
type EventHookOn<T = any = any> = (fn: Callback<T>) => { off: () => void };
```

### `EventHookOff<T = any = any>`

```ts
type EventHookOff<T = any = any> = (fn: Callback<T>) => void;
```

### `EventHookTrigger<T = any = any>`

```ts
type EventHookTrigger<T = any = any> = (...param: Parameters<Callback<T>>) => Promise<unknown[]>;
```

### `EventHookReturn<T>`

```ts
type EventHookReturn<T> = EventHook<T>;
```


---