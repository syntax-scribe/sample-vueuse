[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 9
- **Classes**: 0
- **Imports**: 16
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/integrations/useDrauu/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `EventHookOn` | `@vueuse/core` |
| `MaybeComputedElementRef` | `@vueuse/core` |
| `Fn` | `@vueuse/shared` |
| `Brush` | `drauu` |
| `Drauu` | `drauu` |
| `DrawingMode` | `drauu` |
| `Options` | `drauu` |
| `Ref` | `vue` |
| `ShallowRef` | `vue` |
| `createEventHook` | `@vueuse/core` |
| `unrefElement` | `@vueuse/core` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `createDrauu` | `drauu` |
| `deepRef` | `vue` |
| `shallowRef` | `vue` |
| `watch` | `vue` |


---

## Functions

### `useDrauu(target: MaybeComputedElementRef, options: UseDrauuOptions): UseDrauuReturn`

<details><summary>Code</summary>

```ts
export function useDrauu(
  target: MaybeComputedElementRef,
  options?: UseDrauuOptions,
): UseDrauuReturn {
  const drauuInstance = deepRef<Drauu>()

  let disposables: Fn[] = []

  const onChangedHook = createEventHook<void>()
  const onCanceledHook = createEventHook<void>()
  const onCommittedHook = createEventHook<SVGElement | undefined>()
  const onStartHook = createEventHook<void>()
  const onEndHook = createEventHook<void>()
  const canUndo = shallowRef(false)
  const canRedo = shallowRef(false)
  const altPressed = shallowRef(false)
  const shiftPressed = shallowRef(false)

  const brush = deepRef<Brush>({
    color: 'black',
    size: 3,
    arrowEnd: false,
    cornerRadius: 0,
    dasharray: undefined,
    fill: 'transparent',
    mode: 'draw',
    ...options?.brush,
  })

  watch(brush, () => {
    const instance = drauuInstance.value

    if (instance) {
      instance.brush = brush.value
      instance.mode = brush.value.mode as DrawingMode
    }
  }, { deep: true })

  const undo = () => drauuInstance.value?.undo()
  const redo = () => drauuInstance.value?.redo()
  const clear = () => drauuInstance.value?.clear()
  const cancel = () => drauuInstance.value?.cancel()
  const load = (svg: string) => drauuInstance.value?.load(svg)
  const dump = () => drauuInstance.value?.dump()

  const cleanup = () => {
    disposables.forEach(dispose => dispose())
    drauuInstance.value?.unmount()
  }

  const syncStatus = () => {
    if (drauuInstance.value) {
      canUndo.value = drauuInstance.value.canUndo()
      canRedo.value = drauuInstance.value.canRedo()
      altPressed.value = drauuInstance.value.altPressed
      shiftPressed.value = drauuInstance.value.shiftPressed
    }
  }

  watch(
    () => unrefElement(target),
    (el) => {
      if (!el || typeof SVGSVGElement === 'undefined' || !(el instanceof SVGSVGElement))
        return

      if (drauuInstance.value)
        cleanup()

      drauuInstance.value = createDrauu({ el, ...options })

      syncStatus()

      disposables = [
        drauuInstance.value.on('canceled', () => onCanceledHook.trigger()),
        drauuInstance.value.on('committed', (node: SVGElement | undefined) => onCommittedHook.trigger(node)),
        drauuInstance.value.on('start', () => onStartHook.trigger()),
        drauuInstance.value.on('end', () => onEndHook.trigger()),
        drauuInstance.value.on('changed', () => {
          syncStatus()
          onChangedHook.trigger()
        }),
      ]
    },
    { flush: 'post' },
  )

  tryOnScopeDispose(() => cleanup())

  return {
    drauuInstance,

    load,
    dump,
    clear,
    cancel,
    undo,
    redo,
    canUndo,
    canRedo,
    brush,

    onChanged: onChangedHook.on,
    onCommitted: onCommittedHook.on,
    onStart: onStartHook.on,
    onEnd: onEndHook.on,
    onCanceled: onCanceledHook.on,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive drauu
 *
 * @see https://vueuse.org/useDrauu
 * @param target The target svg element
 * @param options Drauu Options
 */
```

- **Parameters**:
  - `target: MaybeComputedElementRef`
  - `options: UseDrauuOptions`
- **Return Type**: `UseDrauuReturn`
- **Calls**:
  - `deepRef (from vue)`
  - `createEventHook (from @vueuse/core)`
  - `shallowRef (from vue)`
  - `watch (from vue)`
  - `drauuInstance.value?.undo`
  - `drauuInstance.value?.redo`
  - `drauuInstance.value?.clear`
  - `drauuInstance.value?.cancel`
  - `drauuInstance.value?.load`
  - `drauuInstance.value?.dump`
  - `disposables.forEach`
  - `dispose`
  - `drauuInstance.value?.unmount`
  - `drauuInstance.value.canUndo`
  - `drauuInstance.value.canRedo`
  - `unrefElement (from @vueuse/core)`
  - `cleanup`
  - `createDrauu (from drauu)`
  - `syncStatus`
  - `drauuInstance.value.on`
  - `onCanceledHook.trigger`
  - `onCommittedHook.trigger`
  - `onStartHook.trigger`
  - `onEndHook.trigger`
  - `onChangedHook.trigger`
  - `tryOnScopeDispose (from @vueuse/shared)`
### `undo(): any`

<details><summary>Code</summary>

```ts
() => drauuInstance.value?.undo()
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `drauuInstance.value?.undo`
### `redo(): any`

<details><summary>Code</summary>

```ts
() => drauuInstance.value?.redo()
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `drauuInstance.value?.redo`
### `clear(): any`

<details><summary>Code</summary>

```ts
() => drauuInstance.value?.clear()
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `drauuInstance.value?.clear`
### `cancel(): any`

<details><summary>Code</summary>

```ts
() => drauuInstance.value?.cancel()
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `drauuInstance.value?.cancel`
### `load(svg: string): any`

<details><summary>Code</summary>

```ts
(svg: string) => drauuInstance.value?.load(svg)
```
</details>

- **Parameters**:
  - `svg: string`
- **Return Type**: `any`
- **Calls**:
  - `drauuInstance.value?.load`
### `dump(): any`

<details><summary>Code</summary>

```ts
() => drauuInstance.value?.dump()
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `drauuInstance.value?.dump`
### `cleanup(): void`

<details><summary>Code</summary>

```ts
() => {
    disposables.forEach(dispose => dispose())
    drauuInstance.value?.unmount()
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `disposables.forEach`
  - `dispose`
  - `drauuInstance.value?.unmount`
### `syncStatus(): void`

<details><summary>Code</summary>

```ts
() => {
    if (drauuInstance.value) {
      canUndo.value = drauuInstance.value.canUndo()
      canRedo.value = drauuInstance.value.canRedo()
      altPressed.value = drauuInstance.value.altPressed
      shiftPressed.value = drauuInstance.value.shiftPressed
    }
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `drauuInstance.value.canUndo`
  - `drauuInstance.value.canRedo`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseDrauuReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseDrauuReturn {
  drauuInstance: Ref<Drauu | undefined>
  load: (svg: string) => void
  dump: () => string | undefined
  clear: () => void
  cancel: () => void
  undo: () => boolean | undefined
  redo: () => boolean | undefined
  canUndo: ShallowRef<boolean>
  canRedo: ShallowRef<boolean>
  brush: Ref<Brush>

  onChanged: EventHookOn
  onCommitted: EventHookOn
  onStart: EventHookOn
  onEnd: EventHookOn
  onCanceled: EventHookOn
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `drauuInstance` | `Ref<Drauu | undefined>` | ✗ |  |
| `load` | `(svg: string) => void` | ✗ |  |
| `dump` | `() => string | undefined` | ✗ |  |
| `clear` | `() => void` | ✗ |  |
| `cancel` | `() => void` | ✗ |  |
| `undo` | `() => boolean | undefined` | ✗ |  |
| `redo` | `() => boolean | undefined` | ✗ |  |
| `canUndo` | `ShallowRef<boolean>` | ✗ |  |
| `canRedo` | `ShallowRef<boolean>` | ✗ |  |
| `brush` | `Ref<Brush>` | ✗ |  |
| `onChanged` | `EventHookOn` | ✗ |  |
| `onCommitted` | `EventHookOn` | ✗ |  |
| `onStart` | `EventHookOn` | ✗ |  |
| `onEnd` | `EventHookOn` | ✗ |  |
| `onCanceled` | `EventHookOn` | ✗ |  |


---

## Type Aliases

### `UseDrauuOptions`

```ts
type UseDrauuOptions = Omit<Options, 'el'>;
```


---