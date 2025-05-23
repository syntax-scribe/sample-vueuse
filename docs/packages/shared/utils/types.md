[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `types.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 7
- **Interfaces**: 4
- **Type Aliases**: 19

## 🛠️ File Location:
📂 **`packages/shared/utils/types.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


---

## Interfaces

### `Pausable`

<details><summary>Interface Code</summary>

```ts
export interface Pausable {
  /**
   * A ref indicate whether a pausable instance is active
   */
  readonly isActive: Readonly<ShallowRef<boolean>>

  /**
   * Temporary pause the effect from executing
   */
  pause: Fn

  /**
   * Resume the effects
   */
  resume: Fn
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isActive` | `Readonly<ShallowRef<boolean>>` | ✗ |  |
| `pause` | `Fn` | ✗ |  |
| `resume` | `Fn` | ✗ |  |

### `Stoppable<StartFnArgs extends any[] = any[]>`

<details><summary>Interface Code</summary>

```ts
export interface Stoppable<StartFnArgs extends any[] = any[]> {
  /**
   * A ref indicate whether a stoppable instance is executing
   */
  readonly isPending: Readonly<Ref<boolean>>

  /**
   * Stop the effect from executing
   */
  stop: Fn

  /**
   * Start the effects
   */
  start: (...args: StartFnArgs) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isPending` | `Readonly<Ref<boolean>>` | ✗ |  |
| `stop` | `Fn` | ✗ |  |
| `start` | `(...args: StartFnArgs) => void` | ✗ |  |

### `ConfigurableFlush`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableFlush {
  /**
   * Timing for monitoring changes, refer to WatchOptions for more details
   *
   * @default 'pre'
   */
  flush?: WatchOptions['flush']
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `flush` | `WatchOptions['flush']` | ✓ |  |

### `ConfigurableFlushSync`

<details><summary>Interface Code</summary>

```ts
export interface ConfigurableFlushSync {
  /**
   * Timing for monitoring changes, refer to WatchOptions for more details.
   * Unlike `watch()`, the default is set to `sync`
   *
   * @default 'sync'
   */
  flush?: WatchOptions['flush']
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `flush` | `WatchOptions['flush']` | ✓ |  |


---

## Type Aliases

### `Fn`

/**
 * Void function
 */

```ts
type Fn = () => void;
```

### `AnyFn`

/**
 * Any function
 */

```ts
type AnyFn = (...args: any[]) => any;
```

### `RemovableRef<T>`

/**
 * A ref that allow to set null or undefined
 */

```ts
type RemovableRef<T> = Omit<Ref<T>, 'value'> & {
  get value(): T
  set value(value: T | null | undefined)
};
```

### `ReadonlyRefOrGetter<T>`

/**
 * Maybe it's a computed ref, or a readonly value, or a getter function
 */

```ts
type ReadonlyRefOrGetter<T> = ComputedRef<T> | (() => T);
```

### `DeepMaybeRef<T>`

/**
 * Make all the nested attributes of an object or array to MaybeRef<T>
 *
 * Good for accepting options that will be wrapped with `reactive` or `ref`
 *
 * ```ts
 * UnwrapRef<DeepMaybeRef<T>> === T
 * ```
 */

```ts
type DeepMaybeRef<T> = T extends Ref<infer V>
  ? MaybeRef<V>
  : T extends Array<any> | object
    ? { [K in keyof T]: DeepMaybeRef<T[K]> }
    : MaybeRef<T>;
```

### `Arrayable<T>`

```ts
type Arrayable<T> = T[] | T;
```

### `ElementOf<T>`

/**
 * Infers the element type of an array
 */

```ts
type ElementOf<T> = T extends (infer E)[] ? E : never;
```

### `ShallowUnwrapRef<T>`

```ts
type ShallowUnwrapRef<T> = T extends Ref<infer P> ? P : T;
```

### `Awaitable<T>`

```ts
type Awaitable<T> = Promise<T> | T;
```

### `ArgumentsType<T>`

```ts
type ArgumentsType<T> = T extends (...args: infer U) => any ? U : never;
```

### `Awaited<T>`

/**
 * Compatible with versions below TypeScript 4.5 Awaited
 */

```ts
type Awaited<T> = T extends null | undefined ? T : // special case for `null | undefined` when not in `--strictNullChecks` mode
    T extends object & { then: (onfulfilled: infer F, ...args: infer _) => any } ? // `await` only unwraps object types with a callable `then`. Non-object types are not unwrapped
      F extends ((value: infer V, ...args: infer _) => any) ? // if the argument to `then` is callable, extracts the first argument
        Awaited<V> : // recursively unwrap the value
        never : // the argument to `then` was not callable
      T;
```

### `Promisify<T>`

```ts
type Promisify<T> = Promise<Awaited<T>>;
```

### `PromisifyFn<T extends AnyFn extends AnyFn>`

```ts
type PromisifyFn<T extends AnyFn extends AnyFn> = (...args: ArgumentsType<T>) => Promisify<ReturnType<T>>;
```

### `MultiWatchSources`

```ts
type MultiWatchSources = (WatchSource<unknown> | object)[];
```

### `MapSources<T>`

```ts
type MapSources<T> = {
  [K in keyof T]: T[K] extends WatchSource<infer V> ? V : never;
};
```

### `MapOldSources<T, Immediate>`

```ts
type MapOldSources<T, Immediate> = {
  [K in keyof T]: T[K] extends WatchSource<infer V> ? Immediate extends true ? V | undefined : V : never;
};
```

### `Mutable<T>`

```ts
type Mutable<T> = { -readonly [P in keyof T]: T[P] };
```

### `IfAny<T, Y, N>`

```ts
type IfAny<T, Y, N> = 0 extends (1 & T) ? Y : N;
```

### `IsAny<T>`

/**
 * will return `true` if `T` is `any`, or `false` otherwise
 */

```ts
type IsAny<T> = IfAny<T, true, false>;
```


---