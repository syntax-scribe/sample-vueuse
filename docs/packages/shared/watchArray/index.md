[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 🧱 Classes | 0 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 3 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/shared/watchArray/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `WatchOptions` | `vue` |
| `WatchSource` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `oldList` | `T[]` | let/var | `options?.immediate
    ? []
    : [...(typeof source === 'function'
        ? source()
        : Array.isArray(source)
          ? source
          : toValue(source))]` | ✗ |
| `added` | `T[]` | const | `[]` | ✗ |
| `found` | `boolean` | let/var | `false` | ✗ |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `watchArray(source: WatchSource<T[]> | T[], cb: WatchArrayCallback<T[], Immediate extends true ? T[] | undefined : T[]>, options: WatchOptions<Immediate>): any`

<details><summary>Code</summary>

```ts
export function watchArray<T, Immediate extends Readonly<boolean> = false>(
  source: WatchSource<T[]> | T[],
  cb: WatchArrayCallback<T[], Immediate extends true ? T[] | undefined : T[]>,
  options?: WatchOptions<Immediate>,
) {
  let oldList: T[] = options?.immediate
    ? []
    : [...(typeof source === 'function'
        ? source()
        : Array.isArray(source)
          ? source
          : toValue(source))]

  return watch(source as WatchSource<T[]>, (newList, _, onCleanup) => {
    const oldListRemains = Array.from({ length: oldList.length })
    const added: T[] = []
    for (const obj of newList) {
      let found = false
      for (let i = 0; i < oldList.length; i++) {
        if (!oldListRemains[i] && obj === oldList[i]) {
          oldListRemains[i] = true
          found = true
          break
        }
      }
      if (!found)
        added.push(obj)
    }
    const removed = oldList.filter((_, i) => !oldListRemains[i])
    cb(newList, oldList, added, removed, onCleanup)
    oldList = [...newList]
  }, options)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Watch for an array with additions and removals.
 *
 * @see https://vueuse.org/watchArray
 */
```

- **Parameters**:
  - `source: WatchSource<T[]> | T[]`
  - `cb: WatchArrayCallback<T[], Immediate extends true ? T[] | undefined : T[]>`
  - `options: WatchOptions<Immediate>`
- **Return Type**: `any`
- **Calls**:
  - `source`
  - `Array.isArray`
  - `toValue (from vue)`
  - `watch (from vue)`
  - `Array.from`
  - `added.push`
  - `oldList.filter`
  - `cb`

---

## Type Aliases

### `WatchArrayCallback<V = any = any, OV = any = any>`

```ts
type WatchArrayCallback<V = any = any, OV = any = any> = (value: V, oldValue: OV, added: V, removed: OV, onCleanup: (cleanupFn: () => void) => void) => any;
```


---