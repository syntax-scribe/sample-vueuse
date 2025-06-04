[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 10 |
| 📊 Variables & Constants | 5 |
| 📐 Interfaces | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useFileDialog/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `EventHookOn` | `@vueuse/shared` |
| `Ref` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `createEventHook` | `@vueuse/shared` |
| `hasOwn` | `@vueuse/shared` |
| `deepRef` | `vue` |
| `readonly` | `vue` |
| `defaultDocument` | `../_configurable` |
| `unrefElement` | `../unrefElement` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `DEFAULT_OPTIONS` | `UseFileDialogOptions` | const | `{
  multiple: true,
  accept: '*',
  reset: false,
  directory: false,
}` | ✗ |
| `dt` | `DataTransfer` | const | `new DataTransfer()` | ✗ |
| `input` | `HTMLInputElement | undefined` | let/var | `*not shown*` | ✗ |
| `result` | `HTMLInputElement` | const | `event.target as HTMLInputElement` | ✗ |
| `_options` | `{ multiple?: boolean; accept?: string; capture?: string; reset?: boolean; directory?: boolean; initialFiles?: FileList | File[]; input?: MaybeRef<T>; document?: Document; }` | const | `{
      ...DEFAULT_OPTIONS,
      ...options,
      ...localOptions,
    }` | ✗ |


---

## Functions

### `prepareInitialFiles(files: UseFileDialogOptions['initialFiles']): FileList | null`

<details><summary>Code</summary>

```ts
function prepareInitialFiles(files: UseFileDialogOptions['initialFiles']): FileList | null {
  if (!files)
    return null

  if (files instanceof FileList)
    return files

  const dt = new DataTransfer()
  for (const file of files) {
    dt.items.add(file)
  }

  return dt.files
}
```
</details>

- **Parameters**:
  - `files: UseFileDialogOptions['initialFiles']`
- **Return Type**: `FileList | null`
- **Calls**:
  - `dt.items.add`
### `useFileDialog(options: UseFileDialogOptions): UseFileDialogReturn`

<details><summary>Code</summary>

```ts
export function useFileDialog(options: UseFileDialogOptions = {}): UseFileDialogReturn {
  const {
    document = defaultDocument,
  } = options

  const files = deepRef<FileList | null>(prepareInitialFiles(options.initialFiles))
  const { on: onChange, trigger: changeTrigger } = createEventHook()
  const { on: onCancel, trigger: cancelTrigger } = createEventHook()
  let input: HTMLInputElement | undefined
  if (document) {
    input = unrefElement(options.input) || document.createElement('input')
    input.type = 'file'

    input.onchange = (event: Event) => {
      const result = event.target as HTMLInputElement
      files.value = result.files
      changeTrigger(files.value)
    }

    input.oncancel = () => {
      cancelTrigger()
    }
  }

  const reset = () => {
    files.value = null
    if (input && input.value) {
      input.value = ''
      changeTrigger(null)
    }
  }

  const open = (localOptions?: Partial<UseFileDialogOptions>) => {
    if (!input)
      return
    const _options = {
      ...DEFAULT_OPTIONS,
      ...options,
      ...localOptions,
    }
    input.multiple = _options.multiple!
    input.accept = _options.accept!
    // webkitdirectory key is not stabled, maybe replaced in the future.
    input.webkitdirectory = _options.directory!
    if (hasOwn(_options, 'capture'))
      input.capture = _options.capture!
    if (_options.reset)
      reset()
    input.click()
  }

  return {
    files: readonly(files),
    open,
    reset,
    onCancel,
    onChange,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Open file dialog with ease.
 *
 * @see https://vueuse.org/useFileDialog
 * @param options
 */
```

- **Parameters**:
  - `options: UseFileDialogOptions`
- **Return Type**: `UseFileDialogReturn`
- **Calls**:
  - `deepRef (from vue)`
  - `prepareInitialFiles`
  - `createEventHook (from @vueuse/shared)`
  - `unrefElement (from ../unrefElement)`
  - `document.createElement`
  - `changeTrigger`
  - `cancelTrigger`
  - `hasOwn (from @vueuse/shared)`
  - `reset`
  - `input.click`
  - `readonly (from vue)`
- **Internal Comments**:
```
// webkitdirectory key is not stabled, maybe replaced in the future. (x4)
```

### `reset(): void`

<details><summary>Code</summary>

```ts
() => {
    files.value = null
    if (input && input.value) {
      input.value = ''
      changeTrigger(null)
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `changeTrigger`
### `open(localOptions: Partial<UseFileDialogOptions>): void`

<details><summary>Code</summary>

```ts
(localOptions?: Partial<UseFileDialogOptions>) => {
    if (!input)
      return
    const _options = {
      ...DEFAULT_OPTIONS,
      ...options,
      ...localOptions,
    }
    input.multiple = _options.multiple!
    input.accept = _options.accept!
    // webkitdirectory key is not stabled, maybe replaced in the future.
    input.webkitdirectory = _options.directory!
    if (hasOwn(_options, 'capture'))
      input.capture = _options.capture!
    if (_options.reset)
      reset()
    input.click()
  }
```
</details>

- **Parameters**:
  - `localOptions: Partial<UseFileDialogOptions>`
- **Return Type**: `void`
- **Calls**:
  - `hasOwn (from @vueuse/shared)`
  - `reset`
  - `input.click`
- **Internal Comments**:
```
// webkitdirectory key is not stabled, maybe replaced in the future. (x4)
```


---

## Interfaces

### `UseFileDialogOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFileDialogOptions extends ConfigurableDocument {
  /**
   * @default true
   */
  multiple?: boolean
  /**
   * @default '*'
   */
  accept?: string
  /**
   * Select the input source for the capture file.
   * @see [HTMLInputElement Capture](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/capture)
   */
  capture?: string
  /**
   * Reset when open file dialog.
   * @default false
   */
  reset?: boolean
  /**
   * Select directories instead of files.
   * @see [HTMLInputElement webkitdirectory](https://developer.mozilla.org/en-US/docs/Web/API/HTMLInputElement/webkitdirectory)
   * @default false
   */
  directory?: boolean

  /**
   * Initial files to set.
   * @default null
   */
  initialFiles?: Array<File> | FileList

  /**
   * The input element to use for file dialog.
   * @default document.createElement('input')
   */
  input?: MaybeElementRef<HTMLInputElement>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `multiple` | `boolean` | ✓ |  |
| `accept` | `string` | ✓ |  |
| `capture` | `string` | ✓ |  |
| `reset` | `boolean` | ✓ |  |
| `directory` | `boolean` | ✓ |  |
| `initialFiles` | `Array<File> | FileList` | ✓ |  |
| `input` | `MaybeElementRef<HTMLInputElement>` | ✓ |  |

### `UseFileDialogReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseFileDialogReturn {
  files: Ref<FileList | null>
  open: (localOptions?: Partial<UseFileDialogOptions>) => void
  reset: () => void
  onChange: EventHookOn<FileList | null>
  onCancel: EventHookOn
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `files` | `Ref<FileList | null>` | ✗ |  |
| `open` | `(localOptions?: Partial<UseFileDialogOptions>) => void` | ✗ |  |
| `reset` | `() => void` | ✗ |  |
| `onChange` | `EventHookOn<FileList | null>` | ✗ |  |
| `onCancel` | `EventHookOn` | ✗ |  |


---