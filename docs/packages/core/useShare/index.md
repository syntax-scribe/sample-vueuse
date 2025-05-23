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
- **Imports**: 5
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useShare/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `toValue` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useShare(shareOptions: MaybeRefOrGetter<UseShareOptions>, options: ConfigurableNavigator): { isSupported: any; share: (overrideOptions?: MaybeRefOrGetter<UseShareOptions>) => Promise<void>; }`

<details><summary>Code</summary>

```ts
export function useShare(shareOptions: MaybeRefOrGetter<UseShareOptions> = {}, options: ConfigurableNavigator = {}) {
  const { navigator = defaultNavigator } = options

  const _navigator = navigator as NavigatorWithShare
  const isSupported = useSupported(() => _navigator && 'canShare' in _navigator)

  const share = async (overrideOptions: MaybeRefOrGetter<UseShareOptions> = {}) => {
    if (isSupported.value) {
      const data = {
        ...toValue(shareOptions),
        ...toValue(overrideOptions),
      }
      let granted = true

      if (data.files && _navigator.canShare)
        granted = _navigator.canShare({ files: data.files })

      if (granted)
        return _navigator.share!(data)
    }
  }

  return {
    isSupported,
    share,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Web Share API.
 *
 * @see https://vueuse.org/useShare
 * @param shareOptions
 * @param options
 */
```

- **Parameters**:
  - `shareOptions: MaybeRefOrGetter<UseShareOptions>`
  - `options: ConfigurableNavigator`
- **Return Type**: `{ isSupported: any; share: (overrideOptions?: MaybeRefOrGetter<UseShareOptions>) => Promise<void>; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `toValue (from vue)`
  - `_navigator.canShare`
  - `complex_call_1273`
### `share(overrideOptions: MaybeRefOrGetter<UseShareOptions>): Promise<void>`

<details><summary>Code</summary>

```ts
async (overrideOptions: MaybeRefOrGetter<UseShareOptions> = {}) => {
    if (isSupported.value) {
      const data = {
        ...toValue(shareOptions),
        ...toValue(overrideOptions),
      }
      let granted = true

      if (data.files && _navigator.canShare)
        granted = _navigator.canShare({ files: data.files })

      if (granted)
        return _navigator.share!(data)
    }
  }
```
</details>

- **Parameters**:
  - `overrideOptions: MaybeRefOrGetter<UseShareOptions>`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `toValue (from vue)`
  - `_navigator.canShare`
  - `complex_call_1273`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseShareOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseShareOptions {
  title?: string
  files?: File[]
  text?: string
  url?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `title` | `string` | ✓ |  |
| `files` | `File[]` | ✓ |  |
| `text` | `string` | ✓ |  |
| `url` | `string` | ✓ |  |

### `NavigatorWithShare`

<details><summary>Interface Code</summary>

```ts
interface NavigatorWithShare {
  share?: (data: UseShareOptions) => Promise<void>
  canShare?: (data: UseShareOptions) => boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `share` | `(data: UseShareOptions) => Promise<void>` | ✓ |  |
| `canShare` | `(data: UseShareOptions) => boolean` | ✓ |  |


---

## Type Aliases

### `UseShareReturn`

```ts
type UseShareReturn = ReturnType<typeof useShare>;
```


---