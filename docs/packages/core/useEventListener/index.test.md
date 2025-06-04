[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 14 |
| 📊 Variables & Constants | 14 |
| ⚡ Async/Await Patterns | 1 |
| 🟢 Vue Composition API | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)

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

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `options` | `{ capture: boolean; }` | const | `{ capture: true }` | ✗ |
| `stop` | `Fn` | let/var | `*not shown*` | ✗ |
| `target` | `HTMLDivElement` | let/var | `*not shown*` | ✗ |
| `removeSpy` | `MockInstance` | let/var | `*not shown*` | ✗ |
| `addSpy` | `MockInstance` | let/var | `*not shown*` | ✗ |
| `event` | `"click"` | const | `'click'` | ✗ |
| `events` | `string[]` | const | `['click', 'scroll', 'blur', 'resize']` | ✗ |
| `listeners` | `any[]` | const | `[vi.fn(), vi.fn(), vi.fn()]` | ✗ |
| `event` | `"click"` | const | `'click'` | ✗ |
| `listeners` | `any[]` | const | `[vi.fn(), vi.fn(), vi.fn()]` | ✗ |
| `events` | `string[]` | const | `['click', 'scroll', 'blur', 'resize', 'custom-event']` | ✗ |
| `target` | `Ref<HTMLDivElement | null>` | let/var | `*not shown*` | ✗ |
| `listener` | `() => any` | let/var | `*not shown*` | ✗ |
| `el` | `any` | let/var | `target.value` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| await-expression | `testTarget` | nextTick(), nextTick(), nextTick() | *none* |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `computed` | computed | *none* | *none* |
| `computed` | computed | *none* | *none* |


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