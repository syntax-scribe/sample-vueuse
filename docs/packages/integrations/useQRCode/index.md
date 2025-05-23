[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 6
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/integrations/useQRCode/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `isClient` | `@vueuse/shared` |
| `toRef` | `@vueuse/shared` |
| `QRCode` | `qrcode` |
| `shallowRef` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useQRCode(text: MaybeRefOrGetter<string>, options: QRCode.QRCodeToDataURLOptions): any`

<details><summary>Code</summary>

```ts
export function useQRCode(
  text: MaybeRefOrGetter<string>,
  options?: QRCode.QRCodeToDataURLOptions,
) {
  const src = toRef(text)
  const result = shallowRef('')

  watch(
    src,
    async (value) => {
      if (src.value && isClient)
        result.value = await QRCode.toDataURL(value, options)
    },
    { immediate: true },
  )

  return result
}
```
</details>

- **JSDoc**:
```ts
/**
 * Wrapper for qrcode.
 *
 * @see https://vueuse.org/useQRCode
 * @param text
 * @param options
 */
```

- **Parameters**:
  - `text: MaybeRefOrGetter<string>`
  - `options: QRCode.QRCodeToDataURLOptions`
- **Return Type**: `any`
- **Calls**:
  - `toRef (from @vueuse/shared)`
  - `shallowRef (from vue)`
  - `watch (from vue)`
  - `QRCode.toDataURL`

---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---