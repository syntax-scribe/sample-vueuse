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
- **Imports**: 2
- **Interfaces**: 3
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useEyeDropper/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `shallowRef` | `vue` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useEyeDropper(options: UseEyeDropperOptions): { isSupported: any; sRGBHex: any; open: (openOptions?: EyeDropperOpenOptions) => Promise<{ sRGBHex: string; }>; }`

<details><summary>Code</summary>

```ts
export function useEyeDropper(options: UseEyeDropperOptions = {}) {
  const { initialValue = '' } = options
  const isSupported = useSupported(() => typeof window !== 'undefined' && 'EyeDropper' in window)
  const sRGBHex = shallowRef(initialValue)

  async function open(openOptions?: EyeDropperOpenOptions) {
    if (!isSupported.value)
      return
    const eyeDropper: EyeDropper = new (window as any).EyeDropper()
    const result = await eyeDropper.open(openOptions)
    sRGBHex.value = result.sRGBHex
    return result
  }

  return { isSupported, sRGBHex, open }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive [EyeDropper API](https://developer.mozilla.org/en-US/docs/Web/API/EyeDropper_API)
 *
 * @see https://vueuse.org/useEyeDropper
 */
```

- **Parameters**:
  - `options: UseEyeDropperOptions`
- **Return Type**: `{ isSupported: any; sRGBHex: any; open: (openOptions?: EyeDropperOpenOptions) => Promise<{ sRGBHex: string; }>; }`
- **Calls**:
  - `useSupported (from ../useSupported)`
  - `shallowRef (from vue)`
  - `eyeDropper.open`
### `open(openOptions: EyeDropperOpenOptions): Promise<{ sRGBHex: string; }>`

<details><summary>Code</summary>

```ts
async function open(openOptions?: EyeDropperOpenOptions) {
    if (!isSupported.value)
      return
    const eyeDropper: EyeDropper = new (window as any).EyeDropper()
    const result = await eyeDropper.open(openOptions)
    sRGBHex.value = result.sRGBHex
    return result
  }
```
</details>

- **Parameters**:
  - `openOptions: EyeDropperOpenOptions`
- **Return Type**: `Promise<{ sRGBHex: string; }>`
- **Calls**:
  - `eyeDropper.open`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `EyeDropperOpenOptions`

<details><summary>Interface Code</summary>

```ts
export interface EyeDropperOpenOptions {
  /**
   * @see https://developer.mozilla.org/en-US/docs/Web/API/AbortSignal
   */
  signal?: AbortSignal
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `signal` | `AbortSignal` | ✓ |  |

### `EyeDropper`

<details><summary>Interface Code</summary>

```ts
export interface EyeDropper {
  // eslint-disable-next-line ts/no-misused-new
  new(): EyeDropper
  open: (options?: EyeDropperOpenOptions) => Promise<{ sRGBHex: string }>
  [Symbol.toStringTag]: 'EyeDropper'
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `open` | `(options?: EyeDropperOpenOptions) => Promise<{ sRGBHex: string }>` | ✗ |  |
| `[Symbol.toStringTag]` | `'EyeDropper'` | ✗ |  |

### `UseEyeDropperOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseEyeDropperOptions {
  /**
   * Initial sRGBHex.
   *
   * @default ''
   */
  initialValue?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `initialValue` | `string` | ✓ |  |


---

## Type Aliases

### `UseEyeDropperReturn`

```ts
type UseEyeDropperReturn = ReturnType<typeof useEyeDropper>;
```


---