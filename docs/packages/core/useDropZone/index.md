[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 6 |
| 🧱 Classes | 0 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 7 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 2 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useDropZone/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `isClient` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `unref` | `vue` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `counter` | `number` | let/var | `0` | ✗ |
| `isValid` | `boolean` | let/var | `true` | ✗ |
| `_options` | `UseDropZoneOptions` | const | `typeof options === 'function' ? { onDrop: options } : options` | ✗ |
| `multiple` | `boolean` | const | `_options.multiple ?? true` | ✗ |
| `preventDefaultForUnhandled` | `boolean` | const | `_options.preventDefaultForUnhandled ?? false` | ✗ |
| `multipleFilesValid` | `boolean` | const | `multiple || items.length <= 1` | ✗ |
| `dataTransferItemList` | `DataTransferItemList` | const | `event.dataTransfer?.items` | ✗ |


---

## Functions

### `useDropZone(target: MaybeRefOrGetter<HTMLElement | Document | null | undefined>, options: UseDropZoneOptions | UseDropZoneOptions['onDrop']): UseDropZoneReturn`

<details><summary>Code</summary>

```ts
export function useDropZone(
  target: MaybeRefOrGetter<HTMLElement | Document | null | undefined>,
  options: UseDropZoneOptions | UseDropZoneOptions['onDrop'] = {},
): UseDropZoneReturn {
  const isOverDropZone = shallowRef(false)
  const files = shallowRef<File[] | null>(null)
  let counter = 0
  let isValid = true

  if (isClient) {
    const _options = typeof options === 'function' ? { onDrop: options } : options
    const multiple = _options.multiple ?? true
    const preventDefaultForUnhandled = _options.preventDefaultForUnhandled ?? false

    const getFiles = (event: DragEvent) => {
      const list = Array.from(event.dataTransfer?.files ?? [])
      return list.length === 0 ? null : (multiple ? list : [list[0]])
    }

    const checkDataTypes = (types: string[]) => {
      const dataTypes = unref(_options.dataTypes)

      if (typeof dataTypes === 'function')
        return dataTypes(types)

      if (!dataTypes?.length)
        return true

      if (types.length === 0)
        return false

      return types.every(type =>
        dataTypes.some(allowedType => type.includes(allowedType)),
      )
    }

    const checkValidity = (items: DataTransferItemList) => {
      const types = Array.from(items ?? []).map(item => item.type)

      const dataTypesValid = checkDataTypes(types)
      const multipleFilesValid = multiple || items.length <= 1

      return dataTypesValid && multipleFilesValid
    }

    const isSafari = () => (
      /^(?:(?!chrome|android).)*safari/i.test(navigator.userAgent)
      && !('chrome' in window)
    )

    const handleDragEvent = (event: DragEvent, eventType: 'enter' | 'over' | 'leave' | 'drop') => {
      const dataTransferItemList = event.dataTransfer?.items
      isValid = (dataTransferItemList && checkValidity(dataTransferItemList)) ?? false

      if (preventDefaultForUnhandled) {
        event.preventDefault()
      }

      if (!isSafari() && !isValid) {
        if (event.dataTransfer) {
          event.dataTransfer.dropEffect = 'none'
        }
        return
      }

      event.preventDefault()
      if (event.dataTransfer) {
        event.dataTransfer.dropEffect = 'copy'
      }

      const currentFiles = getFiles(event)

      switch (eventType) {
        case 'enter':
          counter += 1
          isOverDropZone.value = true
          _options.onEnter?.(null, event)
          break
        case 'over':
          _options.onOver?.(null, event)
          break
        case 'leave':
          counter -= 1
          if (counter === 0)
            isOverDropZone.value = false
          _options.onLeave?.(null, event)
          break
        case 'drop':
          counter = 0
          isOverDropZone.value = false
          if (isValid) {
            files.value = currentFiles
            _options.onDrop?.(currentFiles, event)
          }
          break
      }
    }

    useEventListener<DragEvent>(target, 'dragenter', event => handleDragEvent(event, 'enter'))
    useEventListener<DragEvent>(target, 'dragover', event => handleDragEvent(event, 'over'))
    useEventListener<DragEvent>(target, 'dragleave', event => handleDragEvent(event, 'leave'))
    useEventListener<DragEvent>(target, 'drop', event => handleDragEvent(event, 'drop'))
  }

  return {
    files,
    isOverDropZone,
  }
}
```
</details>

- **Parameters**:
  - `target: MaybeRefOrGetter<HTMLElement | Document | null | undefined>`
  - `options: UseDropZoneOptions | UseDropZoneOptions['onDrop']`
- **Return Type**: `UseDropZoneReturn`
- **Calls**:
  - `shallowRef (from vue)`
  - `Array.from`
  - `unref (from vue)`
  - `dataTypes`
  - `types.every`
  - `dataTypes.some`
  - `type.includes`
  - `Array.from(items ?? []).map`
  - `checkDataTypes`
  - `/^(?:(?!chrome|android).)*safari/i.test`
  - `checkValidity`
  - `event.preventDefault`
  - `isSafari`
  - `getFiles`
  - `_options.onEnter`
  - `_options.onOver`
  - `_options.onLeave`
  - `_options.onDrop`
  - `useEventListener (from ../useEventListener)`
  - `handleDragEvent`
### `getFiles(event: DragEvent): File[]`

<details><summary>Code</summary>

```ts
(event: DragEvent) => {
      const list = Array.from(event.dataTransfer?.files ?? [])
      return list.length === 0 ? null : (multiple ? list : [list[0]])
    }
```
</details>

- **Parameters**:
  - `event: DragEvent`
- **Return Type**: `File[]`
- **Calls**:
  - `Array.from`
### `checkDataTypes(types: string[]): any`

<details><summary>Code</summary>

```ts
(types: string[]) => {
      const dataTypes = unref(_options.dataTypes)

      if (typeof dataTypes === 'function')
        return dataTypes(types)

      if (!dataTypes?.length)
        return true

      if (types.length === 0)
        return false

      return types.every(type =>
        dataTypes.some(allowedType => type.includes(allowedType)),
      )
    }
```
</details>

- **Parameters**:
  - `types: string[]`
- **Return Type**: `any`
- **Calls**:
  - `unref (from vue)`
  - `dataTypes`
  - `types.every`
  - `dataTypes.some`
  - `type.includes`
### `checkValidity(items: DataTransferItemList): boolean`

<details><summary>Code</summary>

```ts
(items: DataTransferItemList) => {
      const types = Array.from(items ?? []).map(item => item.type)

      const dataTypesValid = checkDataTypes(types)
      const multipleFilesValid = multiple || items.length <= 1

      return dataTypesValid && multipleFilesValid
    }
```
</details>

- **Parameters**:
  - `items: DataTransferItemList`
- **Return Type**: `boolean`
- **Calls**:
  - `Array.from(items ?? []).map`
  - `checkDataTypes`
### `isSafari(): boolean`

<details><summary>Code</summary>

```ts
() => (
      /^(?:(?!chrome|android).)*safari/i.test(navigator.userAgent)
      && !('chrome' in window)
    )
```
</details>

- **Return Type**: `boolean`
### `handleDragEvent(event: DragEvent, eventType: 'enter' | 'over' | 'leave' | 'drop'): void`

<details><summary>Code</summary>

```ts
(event: DragEvent, eventType: 'enter' | 'over' | 'leave' | 'drop') => {
      const dataTransferItemList = event.dataTransfer?.items
      isValid = (dataTransferItemList && checkValidity(dataTransferItemList)) ?? false

      if (preventDefaultForUnhandled) {
        event.preventDefault()
      }

      if (!isSafari() && !isValid) {
        if (event.dataTransfer) {
          event.dataTransfer.dropEffect = 'none'
        }
        return
      }

      event.preventDefault()
      if (event.dataTransfer) {
        event.dataTransfer.dropEffect = 'copy'
      }

      const currentFiles = getFiles(event)

      switch (eventType) {
        case 'enter':
          counter += 1
          isOverDropZone.value = true
          _options.onEnter?.(null, event)
          break
        case 'over':
          _options.onOver?.(null, event)
          break
        case 'leave':
          counter -= 1
          if (counter === 0)
            isOverDropZone.value = false
          _options.onLeave?.(null, event)
          break
        case 'drop':
          counter = 0
          isOverDropZone.value = false
          if (isValid) {
            files.value = currentFiles
            _options.onDrop?.(currentFiles, event)
          }
          break
      }
    }
```
</details>

- **Parameters**:
  - `event: DragEvent`
  - `eventType: 'enter' | 'over' | 'leave' | 'drop'`
- **Return Type**: `void`
- **Calls**:
  - `checkValidity`
  - `event.preventDefault`
  - `isSafari`
  - `getFiles`
  - `_options.onEnter`
  - `_options.onOver`
  - `_options.onLeave`
  - `_options.onDrop`

---

## Interfaces

### `UseDropZoneReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseDropZoneReturn {
  files: ShallowRef<File[] | null>
  isOverDropZone: ShallowRef<boolean>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `files` | `ShallowRef<File[] | null>` | ✗ |  |
| `isOverDropZone` | `ShallowRef<boolean>` | ✗ |  |

### `UseDropZoneOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseDropZoneOptions {
  /**
   * Allowed data types, if not set, all data types are allowed.
   * Also can be a function to check the data types.
   */
  dataTypes?: MaybeRef<readonly string[]> | ((types: readonly string[]) => boolean)
  onDrop?: (files: File[] | null, event: DragEvent) => void
  onEnter?: (files: File[] | null, event: DragEvent) => void
  onLeave?: (files: File[] | null, event: DragEvent) => void
  onOver?: (files: File[] | null, event: DragEvent) => void
  /**
   * Allow multiple files to be dropped. Defaults to true.
   */
  multiple?: boolean
  /**
   * Prevent default behavior for unhandled events. Defaults to false.
   */
  preventDefaultForUnhandled?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `dataTypes` | `MaybeRef<readonly string[]> | ((types: readonly string[]) => boolean)` | ✓ |  |
| `onDrop` | `(files: File[] | null, event: DragEvent) => void` | ✓ |  |
| `onEnter` | `(files: File[] | null, event: DragEvent) => void` | ✓ |  |
| `onLeave` | `(files: File[] | null, event: DragEvent) => void` | ✓ |  |
| `onOver` | `(files: File[] | null, event: DragEvent) => void` | ✓ |  |
| `multiple` | `boolean` | ✓ |  |
| `preventDefaultForUnhandled` | `boolean` | ✓ |  |


---