[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 2
- **Type Aliases**: 12

## 🛠️ File Location:
📂 **`packages/shared/syncRef/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Ref` | `vue` |
| `ConfigurableFlushSync` | `../utils` |
| `WatchPausableReturn` | `../watchPausable` |
| `pausableWatch` | `../watchPausable` |


---

## Functions

### `syncRef(left: Ref<L>, right: Ref<R>, [options]: Equal<L, R> extends true
    ? [options?: SyncRefOptions<L, R, D>]
    : [options: SyncRefOptions<L, R, D>]): () => void`

<details><summary>Code</summary>

```ts
export function syncRef<L, R, D extends Direction = 'both'>(
  left: Ref<L>,
  right: Ref<R>,
  ...[options]: Equal<L, R> extends true
    ? [options?: SyncRefOptions<L, R, D>]
    : [options: SyncRefOptions<L, R, D>]
) {
  const {
    flush = 'sync',
    deep = false,
    immediate = true,
    direction = 'both',
    transform = {},
  } = options || {}

  const watchers: WatchPausableReturn[] = []

  const transformLTR = ('ltr' in transform && transform.ltr) || (v => v)
  const transformRTL = ('rtl' in transform && transform.rtl) || (v => v)

  if (direction === 'both' || direction === 'ltr') {
    watchers.push(pausableWatch(
      left,
      (newValue) => {
        watchers.forEach(w => w.pause())
        right.value = transformLTR(newValue) as R
        watchers.forEach(w => w.resume())
      },
      { flush, deep, immediate },
    ))
  }

  if (direction === 'both' || direction === 'rtl') {
    watchers.push(pausableWatch(
      right,
      (newValue) => {
        watchers.forEach(w => w.pause())
        left.value = transformRTL(newValue) as L
        watchers.forEach(w => w.resume())
      },
      { flush, deep, immediate },
    ))
  }

  const stop = () => {
    watchers.forEach(w => w.stop())
  }

  return stop
}
```
</details>

- **JSDoc**:
```ts
/**
 * Two-way refs synchronization.
 * From the set theory perspective to restrict the option's type
 * Check in the following order:
 * 1. L = R
 * 2. L ∩ R ≠ ∅
 * 3. L ⊆ R
 * 4. L ∩ R = ∅
 */
```

- **Parameters**:
  - `left: Ref<L>`
  - `right: Ref<R>`
  - `[options]: Equal<L, R> extends true
    ? [options?: SyncRefOptions<L, R, D>]
    : [options: SyncRefOptions<L, R, D>]`
- **Return Type**: `() => void`
- **Calls**:
  - `watchers.push`
  - `pausableWatch (from ../watchPausable)`
  - `watchers.forEach`
  - `w.pause`
  - `transformLTR`
  - `w.resume`
  - `transformRTL`
  - `w.stop`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    watchers.forEach(w => w.stop())
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `watchers.forEach`
  - `w.stop`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `EqualType<D extends Direction, L, R, O extends keyof Transform<L, R> = D extends 'both' ? 'ltr' | 'rtl' : D>`

<details><summary>Interface Code</summary>

```ts
interface EqualType<
  D extends Direction,
  L,
  R,
  O extends keyof Transform<L, R> = D extends 'both' ? 'ltr' | 'rtl' : D,
> {
  transform?: SpecificFieldPartial<Pick<Transform<L, R>, O>, O>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `transform` | `SpecificFieldPartial<Pick<Transform<L, R>, O>, O>` | ✓ |  |

### `Transform<L, R>`

<details><summary>Interface Code</summary>

```ts
interface Transform<L, R> {
  ltr: (left: L) => R
  rtl: (right: R) => L
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `ltr` | `(left: L) => R` | ✗ |  |
| `rtl` | `(right: R) => L` | ✗ |  |


---

## Type Aliases

### `Direction`

```ts
type Direction = 'ltr' | 'rtl' | 'both';
```

### `SpecificFieldPartial<T, K extends keyof T extends keyof T>`

```ts
type SpecificFieldPartial<T, K extends keyof T extends keyof T> = Partial<Pick<T, K>> & Omit<T, K>;
```

### `Equal<A, B>`

/**
 * A = B
 */

```ts
type Equal<A, B> = [A] extends [B] ? ([B] extends [A] ? true : false) : false;
```

### `IntersectButNotEqual<A, B>`

/**
 * A ∩ B ≠ ∅
 */

```ts
type IntersectButNotEqual<A, B> = Equal<A, B> extends true
  ? false
  : A & B extends never
    ? false
    : true;
```

### `IncludeButNotEqual<A, B>`

/**
 * A ⊆ B
 */

```ts
type IncludeButNotEqual<A, B> = Equal<A, B> extends true
  ? false
  : A extends B
    ? true
    : false;
```

### `NotIntersect<A, B>`

/**
 * A ∩ B = ∅
 */

```ts
type NotIntersect<A, B> = Equal<A, B> extends true
  ? false
  : A & B extends never
    ? true
    : false;
```

### `StrictIncludeMap<IncludeType extends 'LR' | 'RL' extends 'LR' | 'RL', D extends Exclude<Direction, 'both'> extends Exclude<Direction, 'both'>, L, R>`

```ts
type StrictIncludeMap<IncludeType extends 'LR' | 'RL' extends 'LR' | 'RL', D extends Exclude<Direction, 'both'> extends Exclude<Direction, 'both'>, L, R> = (Equal<[IncludeType, D], ['LR', 'ltr']>
  & Equal<[IncludeType, D], ['RL', 'rtl']>) extends true
  ? {
      transform?: SpecificFieldPartial<Pick<Transform<L, R>, D>, D>
    } : {
      transform: Pick<Transform<L, R>, D>
    };
```

### `StrictIncludeType<IncludeType extends 'LR' | 'RL' extends 'LR' | 'RL', D extends Direction extends Direction, L, R>`

```ts
type StrictIncludeType<IncludeType extends 'LR' | 'RL' extends 'LR' | 'RL', D extends Direction extends Direction, L, R> = D extends 'both'
  ? {
      transform: SpecificFieldPartial<Transform<L, R>, IncludeType extends 'LR' ? 'ltr' : 'rtl'>
    }
  : D extends Exclude<Direction, 'both'>
    ? StrictIncludeMap<IncludeType, D, L, R>
    : never;
```

### `IntersectButNotEqualType<D extends Direction extends Direction, L, R>`

```ts
type IntersectButNotEqualType<D extends Direction extends Direction, L, R> = D extends 'both'
  ? {
      transform: Transform<L, R>
    }
  : D extends Exclude<Direction, 'both'>
    ? {
        transform: Pick<Transform<L, R>, D>
      }
    : never;
```

### `NotIntersectType<D extends Direction extends Direction, L, R>`

```ts
type NotIntersectType<D extends Direction extends Direction, L, R> = IntersectButNotEqualType<D, L, R>;
```

### `TransformType<D extends Direction extends Direction, L, R>`

```ts
type TransformType<D extends Direction extends Direction, L, R> = Equal<L, R> extends true
  // L = R
  ? EqualType<D, L, R>
  : IncludeButNotEqual<L, R> extends true
    // L ⊆ R
    ? StrictIncludeType<'LR', D, L, R>
    : IncludeButNotEqual<R, L> extends true
      // R ⊆ L
      ? StrictIncludeType<'RL', D, L, R>
      : IntersectButNotEqual<L, R> extends true
        // L ∩ R ≠ ∅
        ? IntersectButNotEqualType<D, L, R>
        : NotIntersect<L, R> extends true
          // L ∩ R = ∅
          ? NotIntersectType<D, L, R>
          : never;
```

### `SyncRefOptions<L, R, D extends Direction extends Direction>`

```ts
type SyncRefOptions<L, R, D extends Direction extends Direction> = ConfigurableFlushSync & {
  /**
   * Watch deeply
   *
   * @default false
   */
  deep?: boolean
  /**
   * Sync values immediately
   *
   * @default true
   */
  immediate?: boolean

  /**
   * Direction of syncing. Value will be redefined if you define syncConvertors
   *
   * @default 'both'
   */
  direction?: D
} & TransformType<D, L, R>;
```


---