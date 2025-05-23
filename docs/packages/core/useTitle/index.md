[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 12
- **Interfaces**: 0
- **Type Aliases**: 3

## 🛠️ File Location:
📂 **`packages/core/useTitle/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ReadonlyRefOrGetter` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `toRef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultDocument` | `../_configurable` |
| `useMutationObserver` | `../useMutationObserver` |


---

## Functions

### `useTitle(newTitle: ReadonlyRefOrGetter<string | null | undefined>, options: UseTitleOptions): ComputedRef<string | null | undefined>`

<details><summary>Code</summary>

```ts
export function useTitle(
  newTitle: ReadonlyRefOrGetter<string | null | undefined>,
  options?: UseTitleOptions,
): ComputedRef<string | null | undefined>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive document title.
 *
 * @see https://vueuse.org/useTitle
 * @param newTitle
 * @param options
 * @description It's not SSR compatible. Your value will be applied only on client-side.
 */
```

- **Parameters**:
  - `newTitle: ReadonlyRefOrGetter<string | null | undefined>`
  - `options: UseTitleOptions`
- **Return Type**: `ComputedRef<string | null | undefined>`
### `format(t: string): any`

<details><summary>Code</summary>

```ts
function format(t: string) {
    if (!('titleTemplate' in options))
      return t
    const template = options.titleTemplate || '%s'
    return typeof template === 'function'
      ? template(t)
      : toValue(template).replace(/%s/g, t)
  }
```
</details>

- **Parameters**:
  - `t: string`
- **Return Type**: `any`
- **Calls**:
  - `template`
  - `toValue(template).replace`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `UseTitleOptionsBase`

```ts
type UseTitleOptionsBase = {
  /**
   * Restore the original title when unmounted
   * @param originTitle original title
   * @returns restored title
   */
  restoreOnUnmount?: false | ((originalTitle: string, currentTitle: string) => string | null | undefined)
} & (
  {
    /**
     * Observe `document.title` changes using MutationObserve
     * Cannot be used together with `titleTemplate` option.
     *
     * @default false
     */
    observe?: boolean
  }
  | {
    /**
     * The template string to parse the title (e.g., '%s | My Website')
     * Cannot be used together with `observe` option.
     *
     * @default '%s'
     */
    titleTemplate?: MaybeRef<string> | ((title: string) => string)
  }
);
```

### `UseTitleOptions`

```ts
type UseTitleOptions = ConfigurableDocument & UseTitleOptionsBase;
```

### `UseTitleReturn`

```ts
type UseTitleReturn = ReturnType<typeof useTitle>;
```


---