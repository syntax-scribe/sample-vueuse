[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 14
- **Interfaces**: 0
- **Type Aliases**: 0

## 🛠️ File Location:
📂 **`packages/core/useEventListener/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `MockInstance` | `vitest` |
| `Ref` | `vue` |
| `beforeEach` | `vitest` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `vi` | `vitest` |
| `computed` | `vue` |
| `deepRef` | `vue` |
| `effectScope` | `vue` |
| `nextTick` | `vue` |
| `shallowRef` | `vue` |
| `useEventListener` | `./index` |


---

## Functions

### `getTargetName(useTarget: boolean): "element" | "window"`

<details><summary>Code</summary>

```ts
function getTargetName(useTarget: boolean) {
      return useTarget ? 'element' : 'window'
    }
```
</details>

- **Parameters**:
  - `useTarget: boolean`
- **Return Type**: `"element" | "window"`
### `getArgs(useTarget: boolean): any[]`

<details><summary>Code</summary>

```ts
function getArgs(useTarget: boolean) {
      return (useTarget ? [target, 'click', listener] : ['click', listener])
    }
```
</details>

- **Parameters**:
  - `useTarget: boolean`
- **Return Type**: `any[]`
### `trigger(useTarget: boolean): void`

<details><summary>Code</summary>

```ts
function trigger(useTarget: boolean) {
      (useTarget ? target.value : window)!.dispatchEvent(new MouseEvent('click'))
    }
```
</details>

- **Parameters**:
  - `useTarget: boolean`
- **Return Type**: `void`
- **Calls**:
  - `(useTarget ? target.value : window)!.dispatchEvent`
### `testTarget(useTarget: boolean): void`

<details><summary>Code</summary>

```ts
function testTarget(useTarget: boolean) {
      it(`should ${getTargetName(useTarget)} listen event`, async () => {
        // @ts-expect-error mock different args
        const stop = useEventListener(...getArgs(useTarget))

        trigger(useTarget)

        await nextTick()

        expect(listener).toHaveBeenCalledTimes(1)
      })

      it(`should ${getTargetName(useTarget)} manually stop listening event`, async () => {
        // @ts-expect-error mock different args
        const stop = useEventListener(...getArgs(useTarget))

        stop()

        trigger(useTarget)

        await nextTick()

        expect(listener).toHaveBeenCalledTimes(0)
      })

      it(`should ${getTargetName(useTarget)} auto stop listening event`, async () => {
        const scope = effectScope()
        scope.run(async () => {
        // @ts-expect-error mock different args
          useEventListener(...getArgs(useTarget))
        })

        scope.stop()

        trigger(useTarget)

        await nextTick()

        expect(listener).toHaveBeenCalledTimes(0)
      })
    }
```
</details>

- **Parameters**:
  - `useTarget: boolean`
- **Return Type**: `void`
- **Calls**:
  - `it (from vitest)`
  - `getTargetName`
  - `useEventListener (from ./index)`
  - `getArgs`
  - `trigger`
  - `nextTick (from vue)`
  - `expect(listener).toHaveBeenCalledTimes`
  - `stop`
  - `effectScope (from vue)`
  - `scope.run`
  - `scope.stop`
- **Internal Comments**:
```
// @ts-expect-error mock different args (x7)
```


---

## Classes

> No classes found in this file.


---

## Interfaces

> No interfaces found in this file.


---

## Type Aliases

> No type aliases found in this file.


---