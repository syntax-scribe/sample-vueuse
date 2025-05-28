[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 200 |
| 🧱 Classes | 0 |
| 📦 Imports | 19 |
| 📊 Variables & Constants | 7 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 2 |
| 📐 Interfaces | 4 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)

## 🛠️ File Location:
📂 **`packages/core/useStorage/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Awaitable` | `@vueuse/shared` |
| `ConfigurableEventFilter` | `@vueuse/shared` |
| `ConfigurableFlush` | `@vueuse/shared` |
| `RemovableRef` | `@vueuse/shared` |
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `StorageLike` | `../ssr-handlers` |
| `pausableWatch` | `@vueuse/shared` |
| `tryOnMounted` | `@vueuse/shared` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `getSSRHandler` | `../ssr-handlers` |
| `useEventListener` | `../useEventListener` |
| `guessSerializerType` | `./guess` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `StorageSerializers` | `Record<'boolean' | 'object' | 'number' | 'any' | 'string' | 'map' | 'set' | 'date', Serializer<any>>` | const | `{
  boolean: {
    read: (v: any) => v === 'true',
    write: (v: any) => String(v),
  },
  object: {
    read: (v: any) => JSON.parse(v),
    write: (v: any) => JSON.stringify(v),
  },
  number: {
    read: (v: any) => Number.parseFloat(v),
    write: (v: any) => String(v),
  },
  any: {
    read: (v: any) => v,
    write: (v: any) => String(v),
  },
  string: {
    read: (v: any) => v,
    write: (v: any) => String(v),
  },
  map: {
    read: (v: any) => new Map(JSON.parse(v)),
    write: (v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries())),
  },
  set: {
    read: (v: any) => new Set(JSON.parse(v)),
    write: (v: any) => JSON.stringify(Array.from(v as Set<any>)),
  },
  date: {
    read: (v: any) => new Date(v),
    write: (v: any) => v.toISOString(),
  },
}` | ✓ |
| `customStorageEventName` | `"vueuse-storage"` | const | `'vueuse-storage'` | ✓ |
| `data` | `RemovableRef<T>` | const | `(shallow ? shallowRef : deepRef)(typeof defaults === 'function' ? defaults() : defaults) as RemovableRef<T>` | ✗ |
| `serializer` | `Serializer<any>` | const | `options.serializer ?? StorageSerializers[type]` | ✗ |
| `firstMounted` | `boolean` | let/var | `false` | ✗ |
| `payload` | `{ key: any; oldValue: string; newValue: string; storageArea: Storage; }` | const | `{
        key: keyComputed.value,
        oldValue,
        newValue,
        storageArea: storage as Storage,
      }` | ✗ |
| `rawValue` | `string` | const | `event
      ? event.newValue
      : storage!.getItem(keyComputed.value)` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `watch` | watch | *none* | *none* |


---

## Functions

### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): boolean`

<details><summary>Code</summary>

```ts
(v: any) => v === 'true'
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `boolean`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => JSON.parse(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `JSON.parse`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): number`

<details><summary>Code</summary>

```ts
(v: any) => Number.parseFloat(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `number`
- **Calls**:
  - `Number.parseFloat`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => String(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `String`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Map<unknown, unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Map(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Map<unknown, unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from((v as Map<any, any>).entries()))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Set<unknown>`

<details><summary>Code</summary>

```ts
(v: any) => new Set(JSON.parse(v))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Set<unknown>`
### `write(v: any): string`

<details><summary>Code</summary>

```ts
(v: any) => JSON.stringify(Array.from(v as Set<any>))
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `string`
- **Calls**:
  - `JSON.stringify`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `read(v: any): Date`

<details><summary>Code</summary>

```ts
(v: any) => new Date(v)
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `Date`
### `write(v: any): any`

<details><summary>Code</summary>

```ts
(v: any) => v.toISOString()
```
</details>

- **Parameters**:
  - `v: any`
- **Return Type**: `any`
- **Calls**:
  - `v.toISOString`
### `useStorage(key: MaybeRefOrGetter<string>, defaults: MaybeRefOrGetter<string>, storage: StorageLike, options: UseStorageOptions<string>): RemovableRef<string>`

<details><summary>Code</summary>

```ts
export function useStorage(key: MaybeRefOrGetter<string>, defaults: MaybeRefOrGetter<string>, storage?: StorageLike, options?: UseStorageOptions<string>): RemovableRef<string>
```
</details>

- **Parameters**:
  - `key: MaybeRefOrGetter<string>`
  - `defaults: MaybeRefOrGetter<string>`
  - `storage: StorageLike`
  - `options: UseStorageOptions<string>`
- **Return Type**: `RemovableRef<string>`
### `onStorageEvent(ev: StorageEvent): void`

<details><summary>Code</summary>

```ts
(ev: StorageEvent): void => {
    if (initOnMounted && !firstMounted) {
      return
    }

    update(ev)
  }
```
</details>

- **Parameters**:
  - `ev: StorageEvent`
- **Return Type**: `void`
- **Calls**:
  - `update`
### `onStorageCustomEvent(ev: CustomEvent<StorageEventLike>): void`

<details><summary>Code</summary>

```ts
(ev: CustomEvent<StorageEventLike>): void => {
    if (initOnMounted && !firstMounted) {
      return
    }

    updateFromCustomEvent(ev)
  }
```
</details>

- **Parameters**:
  - `ev: CustomEvent<StorageEventLike>`
- **Return Type**: `void`
- **Calls**:
  - `updateFromCustomEvent`
### `dispatchWriteEvent(oldValue: string | null, newValue: string | null): void`

<details><summary>Code</summary>

```ts
function dispatchWriteEvent(oldValue: string | null, newValue: string | null) {
    // send custom event to communicate within same page
    if (window) {
      const payload = {
        key: keyComputed.value,
        oldValue,
        newValue,
        storageArea: storage as Storage,
      }
      // We also use a CustomEvent since StorageEvent cannot
      // be constructed with a non-built-in storage area
      window.dispatchEvent(storage instanceof Storage
        ? new StorageEvent('storage', payload)
        : new CustomEvent<StorageEventLike>(customStorageEventName, {
          detail: payload,
        }))
    }
  }
```
</details>

- **Parameters**:
  - `oldValue: string | null`
  - `newValue: string | null`
- **Return Type**: `void`
- **Calls**:
  - `window.dispatchEvent`
- **Internal Comments**:
```
// send custom event to communicate within same page
// We also use a CustomEvent since StorageEvent cannot (x4)
// be constructed with a non-built-in storage area (x4)
```

### `write(v: unknown): void`

<details><summary>Code</summary>

```ts
function write(v: unknown) {
    try {
      const oldValue = storage!.getItem(keyComputed.value)

      if (v == null) {
        dispatchWriteEvent(oldValue, null)
        storage!.removeItem(keyComputed.value)
      }
      else {
        const serialized = serializer.write(v as any)
        if (oldValue !== serialized) {
          storage!.setItem(keyComputed.value, serialized)
          dispatchWriteEvent(oldValue, serialized)
        }
      }
    }
    catch (e) {
      onError(e)
    }
  }
```
</details>

- **Parameters**:
  - `v: unknown`
- **Return Type**: `void`
- **Calls**:
  - `storage!.getItem`
  - `dispatchWriteEvent`
  - `storage!.removeItem`
  - `serializer.write`
  - `storage!.setItem`
  - `onError`
### `read(event: StorageEventLike): any`

<details><summary>Code</summary>

```ts
function read(event?: StorageEventLike) {
    const rawValue = event
      ? event.newValue
      : storage!.getItem(keyComputed.value)

    if (rawValue == null) {
      if (writeDefaults && rawInit != null)
        storage!.setItem(keyComputed.value, serializer.write(rawInit))
      return rawInit
    }
    else if (!event && mergeDefaults) {
      const value = serializer.read(rawValue)
      if (typeof mergeDefaults === 'function')
        return mergeDefaults(value, rawInit)
      else if (type === 'object' && !Array.isArray(value))
        return { ...rawInit as any, ...value }
      return value
    }
    else if (typeof rawValue !== 'string') {
      return rawValue
    }
    else {
      return serializer.read(rawValue)
    }
  }
```
</details>

- **Parameters**:
  - `event: StorageEventLike`
- **Return Type**: `any`
- **Calls**:
  - `storage!.getItem`
  - `storage!.setItem`
  - `serializer.write`
  - `serializer.read`
  - `mergeDefaults`
  - `Array.isArray`
### `update(event: StorageEventLike): void`

<details><summary>Code</summary>

```ts
function update(event?: StorageEventLike) {
    if (event && event.storageArea !== storage)
      return

    if (event && event.key == null) {
      data.value = rawInit
      return
    }

    if (event && event.key !== keyComputed.value)
      return

    pauseWatch()
    try {
      if (event?.newValue !== serializer.write(data.value))
        data.value = read(event)
    }
    catch (e) {
      onError(e)
    }
    finally {
      // use nextTick to avoid infinite loop
      if (event)
        nextTick(resumeWatch)
      else
        resumeWatch()
    }
  }
```
</details>

- **Parameters**:
  - `event: StorageEventLike`
- **Return Type**: `void`
- **Calls**:
  - `pauseWatch`
  - `serializer.write`
  - `read`
  - `onError`
  - `nextTick (from vue)`
  - `resumeWatch`
- **Internal Comments**:
```
// use nextTick to avoid infinite loop
```

### `updateFromCustomEvent(event: CustomEvent<StorageEventLike>): void`

<details><summary>Code</summary>

```ts
function updateFromCustomEvent(event: CustomEvent<StorageEventLike>) {
    update(event.detail)
  }
```
</details>

- **Parameters**:
  - `event: CustomEvent<StorageEventLike>`
- **Return Type**: `void`
- **Calls**:
  - `update`

---

## Interfaces

### `Serializer<T>`

<details><summary>Interface Code</summary>

```ts
export interface Serializer<T> {
  read: (raw: string) => T
  write: (value: T) => string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `read` | `(raw: string) => T` | ✗ |  |
| `write` | `(value: T) => string` | ✗ |  |

### `SerializerAsync<T>`

<details><summary>Interface Code</summary>

```ts
export interface SerializerAsync<T> {
  read: (raw: string) => Awaitable<T>
  write: (value: T) => Awaitable<string>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `read` | `(raw: string) => Awaitable<T>` | ✗ |  |
| `write` | `(value: T) => Awaitable<string>` | ✗ |  |

### `StorageEventLike`

<details><summary>Interface Code</summary>

```ts
export interface StorageEventLike {
  storageArea: StorageLike | null
  key: StorageEvent['key']
  oldValue: StorageEvent['oldValue']
  newValue: StorageEvent['newValue']
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `storageArea` | `StorageLike | null` | ✗ |  |
| `key` | `StorageEvent['key']` | ✗ |  |
| `oldValue` | `StorageEvent['oldValue']` | ✗ |  |
| `newValue` | `StorageEvent['newValue']` | ✗ |  |

### `UseStorageOptions<T>`

<details><summary>Interface Code</summary>

```ts
export interface UseStorageOptions<T> extends ConfigurableEventFilter, ConfigurableWindow, ConfigurableFlush {
  /**
   * Watch for deep changes
   *
   * @default true
   */
  deep?: boolean

  /**
   * Listen to storage changes, useful for multiple tabs application
   *
   * @default true
   */
  listenToStorageChanges?: boolean

  /**
   * Write the default value to the storage when it does not exist
   *
   * @default true
   */
  writeDefaults?: boolean

  /**
   * Merge the default value with the value read from the storage.
   *
   * When setting it to true, it will perform a **shallow merge** for objects.
   * You can pass a function to perform custom merge (e.g. deep merge), for example:
   *
   * @default false
   */
  mergeDefaults?: boolean | ((storageValue: T, defaults: T) => T)

  /**
   * Custom data serialization
   */
  serializer?: Serializer<T>

  /**
   * On error callback
   *
   * Default log error to `console.error`
   */
  onError?: (error: unknown) => void

  /**
   * Use shallow ref as reference
   *
   * @default false
   */
  shallow?: boolean

  /**
   * Wait for the component to be mounted before reading the storage.
   *
   * @default false
   */
  initOnMounted?: boolean
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `deep` | `boolean` | ✓ |  |
| `listenToStorageChanges` | `boolean` | ✓ |  |
| `writeDefaults` | `boolean` | ✓ |  |
| `mergeDefaults` | `boolean | ((storageValue: T, defaults: T) => T)` | ✓ |  |
| `serializer` | `Serializer<T>` | ✓ |  |
| `onError` | `(error: unknown) => void` | ✓ |  |
| `shallow` | `boolean` | ✓ |  |
| `initOnMounted` | `boolean` | ✓ |  |


---