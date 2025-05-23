[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 📊 Analysis Summary

- **Functions**: 6
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 2
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useClipboard/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `useTimeoutFn` | `@vueuse/shared` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `usePermission` | `../usePermission` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useClipboard(options: UseClipboardOptions<undefined>): UseClipboardReturn<false>`

<details><summary>Code</summary>

```ts
export function useClipboard(options?: UseClipboardOptions<undefined>): UseClipboardReturn<false>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Clipboard API.
 *
 * @see https://vueuse.org/useClipboard
 * @param options
 */
```

- **Parameters**:
  - `options: UseClipboardOptions<undefined>`
- **Return Type**: `UseClipboardReturn<false>`
### `updateText(): Promise<void>`

<details><summary>Code</summary>

```ts
async function updateText() {
    let useLegacy = !(isClipboardApiSupported.value && isAllowed(permissionRead.value))
    if (!useLegacy) {
      try {
        text.value = await navigator!.clipboard.readText()
      }
      catch {
        useLegacy = true
      }
    }
    if (useLegacy) {
      text.value = legacyRead()
    }
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `isAllowed`
  - `navigator!.clipboard.readText`
  - `legacyRead`
### `copy(value: any): Promise<void>`

<details><summary>Code</summary>

```ts
async function copy(value = toValue(source)) {
    if (isSupported.value && value != null) {
      let useLegacy = !(isClipboardApiSupported.value && isAllowed(permissionWrite.value))
      if (!useLegacy) {
        try {
          await navigator!.clipboard.writeText(value)
        }
        catch {
          useLegacy = true
        }
      }
      if (useLegacy)
        legacyCopy(value)

      text.value = value
      copied.value = true
      timeout.start()
    }
  }
```
</details>

- **Parameters**:
  - `value: any`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `isAllowed`
  - `navigator!.clipboard.writeText`
  - `legacyCopy`
  - `timeout.start`
### `legacyCopy(value: string): void`

<details><summary>Code</summary>

```ts
function legacyCopy(value: string) {
    const ta = document.createElement('textarea')
    ta.value = value ?? ''
    ta.style.position = 'absolute'
    ta.style.opacity = '0'
    document.body.appendChild(ta)
    ta.select()
    document.execCommand('copy')
    ta.remove()
  }
```
</details>

- **Parameters**:
  - `value: string`
- **Return Type**: `void`
- **Calls**:
  - `document.createElement`
  - `document.body.appendChild`
  - `ta.select`
  - `document.execCommand`
  - `ta.remove`
### `legacyRead(): string`

<details><summary>Code</summary>

```ts
function legacyRead() {
    return document?.getSelection?.()?.toString() ?? ''
  }
```
</details>

- **Return Type**: `string`
- **Calls**:
  - `document?.getSelection?.()?.toString`
### `isAllowed(status: PermissionState | undefined): boolean`

<details><summary>Code</summary>

```ts
function isAllowed(status: PermissionState | undefined) {
    return status === 'granted' || status === 'prompt'
  }
```
</details>

- **Parameters**:
  - `status: PermissionState | undefined`
- **Return Type**: `boolean`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseClipboardOptions<Source>`

<details><summary>Interface Code</summary>

```ts
export interface UseClipboardOptions<Source> extends ConfigurableNavigator {
  /**
   * Enabled reading for clipboard
   *
   * @default false
   */
  read?: boolean

  /**
   * Copy source
   */
  source?: Source

  /**
   * Milliseconds to reset state of `copied` ref
   *
   * @default 1500
   */
  copiedDuring?: number

  /**
   * Whether fallback to document.execCommand('copy') if clipboard is undefined.
   *
   * @default false
   */
  legacy?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `read` | `boolean` | ✓ |  |
| `source` | `Source` | ✓ |  |
| `copiedDuring` | `number` | ✓ |  |
| `legacy` | `boolean` | ✓ |  |

### `UseClipboardReturn<Optional>`

<details><summary>Interface Code</summary>

```ts
export interface UseClipboardReturn<Optional> {
  isSupported: ComputedRef<boolean>
  text: ComputedRef<string>
  copied: ComputedRef<boolean>
  copy: Optional extends true ? (text?: string) => Promise<void> : (text: string) => Promise<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `text` | `ComputedRef<string>` | ✗ |  |
| `copied` | `ComputedRef<boolean>` | ✗ |  |
| `copy` | `Optional extends true ? (text?: string) => Promise<void> : (text: string) => Promise<void>` | ✗ |  |


---

## Type Aliases

> No type aliases found in this file.


---