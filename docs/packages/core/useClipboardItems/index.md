[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 3 |
| 🧱 Classes | 0 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 2 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useClipboardItems/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableNavigator` | `../_configurable` |
| `useTimeoutFn` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `defaultNavigator` | `../_configurable` |
| `useEventListener` | `../useEventListener` |
| `useSupported` | `../useSupported` |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `updateContent` | *none* | navigator!.clipboard.read().then |
| async-function | `copy` | navigator!.clipboard.write(value) | *none* |


---

## Functions

### `useClipboardItems(options: UseClipboardItemsOptions<undefined>): UseClipboardItemsReturn<false>`

<details><summary>Code</summary>

```ts
export function useClipboardItems(options?: UseClipboardItemsOptions<undefined>): UseClipboardItemsReturn<false>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive Clipboard API.
 *
 * @see https://vueuse.org/useClipboardItems
 * @param options
 */
```

- **Parameters**:
  - `options: UseClipboardItemsOptions<undefined>`
- **Return Type**: `UseClipboardItemsReturn<false>`
### `updateContent(): void`

<details><summary>Code</summary>

```ts
function updateContent() {
    if (isSupported.value) {
      navigator!.clipboard.read().then((items) => {
        content.value = items
      })
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `navigator!.clipboard.read().then`
### `copy(value: any): Promise<void>`

<details><summary>Code</summary>

```ts
async function copy(value = toValue(source)) {
    if (isSupported.value && value != null) {
      await navigator!.clipboard.write(value)

      content.value = value
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
  - `navigator!.clipboard.write`
  - `timeout.start`

---

## Interfaces

### `UseClipboardItemsOptions<Source>`

<details><summary>Interface Code</summary>

```ts
export interface UseClipboardItemsOptions<Source> extends ConfigurableNavigator {
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
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `read` | `boolean` | ✓ |  |
| `source` | `Source` | ✓ |  |
| `copiedDuring` | `number` | ✓ |  |

### `UseClipboardItemsReturn<Optional>`

<details><summary>Interface Code</summary>

```ts
export interface UseClipboardItemsReturn<Optional> {
  isSupported: ComputedRef<boolean>
  content: ComputedRef<ClipboardItems>
  copied: ComputedRef<boolean>
  copy: Optional extends true ? (content?: ClipboardItems) => Promise<void> : (text: ClipboardItems) => Promise<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `content` | `ComputedRef<ClipboardItems>` | ✗ |  |
| `copied` | `ComputedRef<boolean>` | ✗ |  |
| `copy` | `Optional extends true ? (content?: ClipboardItems) => Promise<void> : (text: ClipboardItems) => Promise<void>` | ✗ |  |


---