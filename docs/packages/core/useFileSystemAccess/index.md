[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 7
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 6
- **Type Aliases**: 4

## 🛠️ File Location:
📂 **`packages/core/useFileSystemAccess/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Awaitable` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `computed` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useFileSystemAccess(): UseFileSystemAccessReturn<string | ArrayBuffer | Blob>`

<details><summary>Code</summary>

```ts
export function useFileSystemAccess(): UseFileSystemAccessReturn<string | ArrayBuffer | Blob>
```
</details>

- **JSDoc**:
```ts
/**
 * Create and read and write local files.
 * @see https://vueuse.org/useFileSystemAccess
 */
```

- **Return Type**: `UseFileSystemAccessReturn<string | ArrayBuffer | Blob>`
### `open(_options: UseFileSystemAccessCommonOptions): Promise<void>`

<details><summary>Code</summary>

```ts
async function open(_options: UseFileSystemAccessCommonOptions = {}) {
    if (!isSupported.value)
      return
    const [handle] = await window.showOpenFilePicker({ ...toValue(options), ..._options })
    fileHandle.value = handle
    await updateData()
  }
```
</details>

- **Parameters**:
  - `_options: UseFileSystemAccessCommonOptions`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `window.showOpenFilePicker`
  - `toValue (from vue)`
  - `updateData`
### `create(_options: UseFileSystemAccessShowSaveFileOptions): Promise<void>`

<details><summary>Code</summary>

```ts
async function create(_options: UseFileSystemAccessShowSaveFileOptions = {}) {
    if (!isSupported.value)
      return
    fileHandle.value = await (window as FileSystemAccessWindow).showSaveFilePicker({ ...options, ..._options })
    data.value = undefined
    await updateData()
  }
```
</details>

- **Parameters**:
  - `_options: UseFileSystemAccessShowSaveFileOptions`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `(window as FileSystemAccessWindow).showSaveFilePicker`
  - `updateData`
### `save(_options: UseFileSystemAccessShowSaveFileOptions): Promise<void>`

<details><summary>Code</summary>

```ts
async function save(_options: UseFileSystemAccessShowSaveFileOptions = {}) {
    if (!isSupported.value)
      return

    if (!fileHandle.value)
    // save as
      return saveAs(_options)

    if (data.value) {
      const writableStream = await fileHandle.value.createWritable()
      await writableStream.write(data.value)
      await writableStream.close()
    }
    await updateFile()
  }
```
</details>

- **Parameters**:
  - `_options: UseFileSystemAccessShowSaveFileOptions`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `saveAs`
  - `fileHandle.value.createWritable`
  - `writableStream.write`
  - `writableStream.close`
  - `updateFile`
- **Internal Comments**:
```
// save as
```

### `saveAs(_options: UseFileSystemAccessShowSaveFileOptions): Promise<void>`

<details><summary>Code</summary>

```ts
async function saveAs(_options: UseFileSystemAccessShowSaveFileOptions = {}) {
    if (!isSupported.value)
      return

    fileHandle.value = await (window as FileSystemAccessWindow).showSaveFilePicker({ ...options, ..._options })

    if (data.value) {
      const writableStream = await fileHandle.value.createWritable()
      await writableStream.write(data.value)
      await writableStream.close()
    }

    await updateFile()
  }
```
</details>

- **Parameters**:
  - `_options: UseFileSystemAccessShowSaveFileOptions`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `(window as FileSystemAccessWindow).showSaveFilePicker`
  - `fileHandle.value.createWritable`
  - `writableStream.write`
  - `writableStream.close`
  - `updateFile`
### `updateFile(): Promise<void>`

<details><summary>Code</summary>

```ts
async function updateFile() {
    file.value = await fileHandle.value?.getFile()
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `fileHandle.value?.getFile`
### `updateData(): Promise<void>`

<details><summary>Code</summary>

```ts
async function updateData() {
    await updateFile()
    const type = toValue(dataType)
    if (type === 'Text')
      data.value = await file.value?.text()
    else if (type === 'ArrayBuffer')
      data.value = await file.value?.arrayBuffer()
    else if (type === 'Blob')
      data.value = file.value
  }
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `updateFile`
  - `toValue (from vue)`
  - `file.value?.text`
  - `file.value?.arrayBuffer`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `FileSystemAccessShowOpenFileOptions`

<details><summary>Interface Code</summary>

```ts
export interface FileSystemAccessShowOpenFileOptions {
  multiple?: boolean
  types?: Array<{
    description?: string
    accept: Record<string, string[]>
  }>
  excludeAcceptAllOption?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `multiple` | `boolean` | ✓ |  |
| `types` | `Array<{
    description?: string
    accept: Record<string, string[]>
  }>` | ✓ |  |
| `excludeAcceptAllOption` | `boolean` | ✓ |  |

### `FileSystemAccessShowSaveFileOptions`

<details><summary>Interface Code</summary>

```ts
export interface FileSystemAccessShowSaveFileOptions {
  suggestedName?: string
  types?: Array<{
    description?: string
    accept: Record<string, string[]>
  }>
  excludeAcceptAllOption?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `suggestedName` | `string` | ✓ |  |
| `types` | `Array<{
    description?: string
    accept: Record<string, string[]>
  }>` | ✓ |  |
| `excludeAcceptAllOption` | `boolean` | ✓ |  |

### `FileSystemFileHandle`

<details><summary>Interface Code</summary>

```ts
export interface FileSystemFileHandle {
  getFile: () => Promise<File>
  createWritable: () => FileSystemWritableFileStream
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `getFile` | `() => Promise<File>` | ✗ |  |
| `createWritable` | `() => FileSystemWritableFileStream` | ✗ |  |

### `FileSystemWritableFileStream`

<details><summary>Interface Code</summary>

```ts
interface FileSystemWritableFileStream extends WritableStream {
  /**
   * @see https://developer.mozilla.org/en-US/docs/Web/API/FileSystemWritableFileStream/write
   */
  write: FileSystemWritableFileStreamWrite
  /**
   * @see https://developer.mozilla.org/en-US/docs/Web/API/FileSystemWritableFileStream/seek
   */
  seek: (position: number) => Promise<void>
  /**
   * @see https://developer.mozilla.org/en-US/docs/Web/API/FileSystemWritableFileStream/truncate
   */
  truncate: (size: number) => Promise<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `write` | `FileSystemWritableFileStreamWrite` | ✗ |  |
| `seek` | `(position: number) => Promise<void>` | ✗ |  |
| `truncate` | `(size: number) => Promise<void>` | ✗ |  |

### `FileSystemWritableFileStreamWrite`

<details><summary>Interface Code</summary>

```ts
interface FileSystemWritableFileStreamWrite {
  (data: string | BufferSource | Blob): Promise<void>
  (options: { type: 'write', position: number, data: string | BufferSource | Blob }): Promise<void>
  (options: { type: 'seek', position: number }): Promise<void>
  (options: { type: 'truncate', size: number }): Promise<void>
}
```
</details>

### `UseFileSystemAccessReturn<T = string>`

<details><summary>Interface Code</summary>

```ts
export interface UseFileSystemAccessReturn<T = string> {
  isSupported: ComputedRef<boolean>
  data: ShallowRef<T | undefined>
  file: ShallowRef<File | undefined>
  fileName: ComputedRef<string>
  fileMIME: ComputedRef<string>
  fileSize: ComputedRef<number>
  fileLastModified: ComputedRef<number>
  open: (_options?: UseFileSystemAccessCommonOptions) => Awaitable<void>
  create: (_options?: UseFileSystemAccessShowSaveFileOptions) => Awaitable<void>
  save: (_options?: UseFileSystemAccessShowSaveFileOptions) => Awaitable<void>
  saveAs: (_options?: UseFileSystemAccessShowSaveFileOptions) => Awaitable<void>
  updateData: () => Awaitable<void>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `isSupported` | `ComputedRef<boolean>` | ✗ |  |
| `data` | `ShallowRef<T | undefined>` | ✗ |  |
| `file` | `ShallowRef<File | undefined>` | ✗ |  |
| `fileName` | `ComputedRef<string>` | ✗ |  |
| `fileMIME` | `ComputedRef<string>` | ✗ |  |
| `fileSize` | `ComputedRef<number>` | ✗ |  |
| `fileLastModified` | `ComputedRef<number>` | ✗ |  |
| `open` | `(_options?: UseFileSystemAccessCommonOptions) => Awaitable<void>` | ✗ |  |
| `create` | `(_options?: UseFileSystemAccessShowSaveFileOptions) => Awaitable<void>` | ✗ |  |
| `save` | `(_options?: UseFileSystemAccessShowSaveFileOptions) => Awaitable<void>` | ✗ |  |
| `saveAs` | `(_options?: UseFileSystemAccessShowSaveFileOptions) => Awaitable<void>` | ✗ |  |
| `updateData` | `() => Awaitable<void>` | ✗ |  |


---

## Type Aliases

### `FileSystemAccessWindow`

/**
 * FileStream.write
 * @see https://developer.mozilla.org/en-US/docs/Web/API/FileSystemWritableFileStream/write
 */

```ts
type FileSystemAccessWindow = Window & {
  showSaveFilePicker: (options: FileSystemAccessShowSaveFileOptions) => Promise<FileSystemFileHandle>
  showOpenFilePicker: (options: FileSystemAccessShowOpenFileOptions) => Promise<FileSystemFileHandle[]>
};
```

### `UseFileSystemAccessCommonOptions`

```ts
type UseFileSystemAccessCommonOptions = Pick<FileSystemAccessShowOpenFileOptions, 'types' | 'excludeAcceptAllOption'>;
```

### `UseFileSystemAccessShowSaveFileOptions`

```ts
type UseFileSystemAccessShowSaveFileOptions = Pick<FileSystemAccessShowSaveFileOptions, 'suggestedName'>;
```

### `UseFileSystemAccessOptions`

```ts
type UseFileSystemAccessOptions = ConfigurableWindow & UseFileSystemAccessCommonOptions & {
  /**
   * file data type
   */
  dataType?: MaybeRefOrGetter<'Text' | 'ArrayBuffer' | 'Blob'>
};
```


---