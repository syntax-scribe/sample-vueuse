[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 6 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 1 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

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

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `useQRCode` | QRCode.toDataURL(value, options) | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


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