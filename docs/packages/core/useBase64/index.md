[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 🧱 Classes | 0 |
| 📦 Imports | 8 |
| 📊 Variables & Constants | 4 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 3 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 4 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useBase64/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ShallowRef` | `vue` |
| `isClient` | `@vueuse/shared` |
| `isRef` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `getDefaultSerialization` | `./serialization` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `img` | `HTMLImageElement` | const | `_target.cloneNode(false) as HTMLImageElement` | ✗ |
| `ctx` | `CanvasRenderingContext2D` | const | `canvas.getContext('2d')!` | ✗ |
| `_serializeFn` | `any` | const | `options?.serializer || getDefaultSerialization(_target)` | ✗ |
| `fr` | `FileReader` | const | `new FileReader()` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| promise-chain | `execute` | *none* | new Promise(...), imgLoaded(img).then(() => {
            const canvas = document.createElement('canvas')
            const ctx = canvas.getContext('2d')!
            canvas.width = img.width
            canvas.height = img.height
            ctx.drawImage(img, 0, 0, canvas.width, canvas.height)
            resolve(canvas.toDataURL(options?.type, options?.quality))
          }).catch, imgLoaded(img).then, promise.value.then |
| promise-chain | `imgLoaded` | *none* | new Promise(...) |
| promise-chain | `blobToBase64` | *none* | new Promise(...) |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useBase64(target: MaybeRefOrGetter<string | undefined>, options: UseBase64Options): UseBase64Return`

<details><summary>Code</summary>

```ts
export function useBase64(target: MaybeRefOrGetter<string | undefined>, options?: UseBase64Options): UseBase64Return
```
</details>

- **Parameters**:
  - `target: MaybeRefOrGetter<string | undefined>`
  - `options: UseBase64Options`
- **Return Type**: `UseBase64Return`
### `execute(): any`

<details><summary>Code</summary>

```ts
function execute() {
    if (!isClient)
      return

    promise.value = new Promise<string>((resolve, reject) => {
      try {
        const _target = toValue(target)
        if (_target == null) {
          resolve('')
        }
        else if (typeof _target === 'string') {
          resolve(blobToBase64(new Blob([_target], { type: 'text/plain' })))
        }
        else if (_target instanceof Blob) {
          resolve(blobToBase64(_target))
        }
        else if (_target instanceof ArrayBuffer) {
          resolve(window.btoa(String.fromCharCode(...new Uint8Array(_target))))
        }
        else if (_target instanceof HTMLCanvasElement) {
          resolve(_target.toDataURL(options?.type, options?.quality))
        }
        else if (_target instanceof HTMLImageElement) {
          const img = _target.cloneNode(false) as HTMLImageElement
          img.crossOrigin = 'Anonymous'
          imgLoaded(img).then(() => {
            const canvas = document.createElement('canvas')
            const ctx = canvas.getContext('2d')!
            canvas.width = img.width
            canvas.height = img.height
            ctx.drawImage(img, 0, 0, canvas.width, canvas.height)
            resolve(canvas.toDataURL(options?.type, options?.quality))
          }).catch(reject)
        }
        else if (typeof _target === 'object') {
          const _serializeFn = options?.serializer || getDefaultSerialization(_target)

          const serialized = _serializeFn(_target)

          return resolve(blobToBase64(new Blob([serialized], { type: 'application/json' })))
        }
        else {
          reject(new Error('target is unsupported types'))
        }
      }
      catch (error) {
        reject(error)
      }
    })

    promise.value.then((res) => {
      base64.value = options?.dataUrl === false
        ? res.replace(/^data:.*?;base64,/, '')
        : res
    })
    return promise.value
  }
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `toValue (from vue)`
  - `resolve`
  - `blobToBase64`
  - `window.btoa`
  - `String.fromCharCode`
  - `_target.toDataURL`
  - `_target.cloneNode`
  - `imgLoaded(img).then(() => {
            const canvas = document.createElement('canvas')
            const ctx = canvas.getContext('2d')!
            canvas.width = img.width
            canvas.height = img.height
            ctx.drawImage(img, 0, 0, canvas.width, canvas.height)
            resolve(canvas.toDataURL(options?.type, options?.quality))
          }).catch`
  - `getDefaultSerialization (from ./serialization)`
  - `_serializeFn`
  - `reject`
  - `promise.value.then`
  - `res.replace`
### `imgLoaded(img: HTMLImageElement): Promise<void>`

<details><summary>Code</summary>

```ts
function imgLoaded(img: HTMLImageElement) {
  return new Promise<void>((resolve, reject) => {
    if (!img.complete) {
      img.onload = () => {
        resolve()
      }
      img.onerror = reject
    }
    else {
      resolve()
    }
  })
}
```
</details>

- **Parameters**:
  - `img: HTMLImageElement`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `resolve`
### `blobToBase64(blob: Blob): Promise<string>`

<details><summary>Code</summary>

```ts
function blobToBase64(blob: Blob) {
  return new Promise<string>((resolve, reject) => {
    const fr = new FileReader()
    fr.onload = (e) => {
      resolve(e.target!.result as string)
    }
    fr.onerror = reject
    fr.readAsDataURL(blob)
  })
}
```
</details>

- **Parameters**:
  - `blob: Blob`
- **Return Type**: `Promise<string>`
- **Calls**:
  - `resolve`
  - `fr.readAsDataURL`

---

## Interfaces

### `UseBase64Options`

<details><summary>Interface Code</summary>

```ts
export interface UseBase64Options {
  /**
   * Output as Data URL format
   *
   * @default true
   */
  dataUrl?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `dataUrl` | `boolean` | ✓ |  |

### `ToDataURLOptions`

<details><summary>Interface Code</summary>

```ts
export interface ToDataURLOptions extends UseBase64Options {
  /**
   * MIME type
   */
  type?: string | undefined
  /**
   * Image quality of jpeg or webp
   */
  quality?: any
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `type` | `string | undefined` | ✓ |  |
| `quality` | `any` | ✓ |  |

### `UseBase64ObjectOptions<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseBase64ObjectOptions<T> extends UseBase64Options {
  serializer?: (v: T) => string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `serializer` | `(v: T) => string` | ✓ |  |

### `UseBase64Return`

<details><summary>Interface Code</summary>

```ts
export interface UseBase64Return {
  base64: ShallowRef<string>
  promise: ShallowRef<Promise<string>>
  execute: () => Promise<string>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `base64` | `ShallowRef<string>` | ✗ |  |
| `promise` | `ShallowRef<Promise<string>>` | ✗ |  |
| `execute` | `() => Promise<string>` | ✗ |  |


---