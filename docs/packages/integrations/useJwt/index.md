[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 2
- **Classes**: 0
- **Imports**: 8
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/integrations/useJwt/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `JwtDecodeOptions` | `jwt-decode` |
| `JwtHeader` | `jwt-decode` |
| `JwtPayload` | `jwt-decode` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `jwtDecode` | `jwt-decode` |
| `computed` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `useJwt(encodedJwt: MaybeRefOrGetter<string>, options: UseJwtOptions<Fallback>): UseJwtReturn<Payload, Header, Fallback>`

<details><summary>Code</summary>

```ts
export function useJwt<
  Payload extends object = JwtPayload,
  Header extends object = JwtHeader,
  Fallback = null,
>(
  encodedJwt: MaybeRefOrGetter<string>,
  options: UseJwtOptions<Fallback> = {},
): UseJwtReturn<Payload, Header, Fallback> {
  const {
    onError,
    fallbackValue = null,
  } = options

  const decodeWithFallback = <T extends object>(encodedJwt: string, options?: JwtDecodeOptions): T | Fallback => {
    try {
      return jwtDecode<T>(encodedJwt, options)
    }
    catch (err) {
      onError?.(err)
      return fallbackValue as Fallback
    }
  }

  const header = computed(() => decodeWithFallback<Header>(toValue(encodedJwt), { header: true }))
  const payload = computed(() => decodeWithFallback<Payload>(toValue(encodedJwt)))

  return {
    header,
    payload,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive decoded jwt token.
 *
 * @see https://vueuse.org/useJwt
 */
```

- **Parameters**:
  - `encodedJwt: MaybeRefOrGetter<string>`
  - `options: UseJwtOptions<Fallback>`
- **Return Type**: `UseJwtReturn<Payload, Header, Fallback>`
- **Calls**:
  - `jwtDecode (from jwt-decode)`
  - `onError`
  - `computed (from vue)`
  - `decodeWithFallback`
  - `toValue (from vue)`
### `decodeWithFallback(encodedJwt: string, options: JwtDecodeOptions): T | Fallback`

<details><summary>Code</summary>

```ts
<T extends object>(encodedJwt: string, options?: JwtDecodeOptions): T | Fallback => {
    try {
      return jwtDecode<T>(encodedJwt, options)
    }
    catch (err) {
      onError?.(err)
      return fallbackValue as Fallback
    }
  }
```
</details>

- **Parameters**:
  - `encodedJwt: string`
  - `options: JwtDecodeOptions`
- **Return Type**: `T | Fallback`
- **Calls**:
  - `jwtDecode (from jwt-decode)`
  - `onError`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseJwtOptions<Fallback>`

<details><summary>Interface Code</summary>

```ts
export interface UseJwtOptions<Fallback> {
  /**
   * Value returned when encounter error on decoding
   *
   * @default null
   */
  fallbackValue?: Fallback

  /**
   * Error callback for decoding
   */
  onError?: (error: unknown) => void
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `fallbackValue` | `Fallback` | ✓ |  |
| `onError` | `(error: unknown) => void` | ✓ |  |

### `UseJwtReturn<Payload, Header, Fallback>`

<details><summary>Interface Code</summary>

```ts
export interface UseJwtReturn<Payload, Header, Fallback> {
  header: ComputedRef<Header | Fallback>
  payload: ComputedRef<Payload | Fallback>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `header` | `ComputedRef<Header | Fallback>` | ✗ |  |
| `payload` | `ComputedRef<Payload | Fallback>` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---