[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

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

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


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