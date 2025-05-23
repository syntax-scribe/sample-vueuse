[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 1
- **Classes**: 0
- **Imports**: 4
- **Interfaces**: 0
- **Type Aliases**: 1

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

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

### `WatchArrayCallback<V = any = any, OV = any = any>`

```ts
type WatchArrayCallback<V = any = any, OV = any = any> = (value: V, oldValue: OV, added: V, removed: OV, onCleanup: (cleanupFn: () => void) => void) => any;
```


---