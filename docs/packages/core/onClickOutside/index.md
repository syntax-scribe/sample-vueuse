[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 10 |
| 📦 Imports | 12 |
| 📊 Variables & Constants | 8 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/onClickOutside/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Fn` | `@vueuse/shared` |
| `ComponentPublicInstance` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `VNode` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `MaybeElementRef` | `../unrefElement` |
| `isIOS` | `@vueuse/shared` |
| `noop` | `@vueuse/shared` |
| `toValue` | `vue` |
| `defaultWindow` | `../_configurable` |
| `unrefElement` | `../unrefElement` |
| `useEventListener` | `../useEventListener` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `_iOSWorkaround` | `boolean` | let/var | `false` | ✗ |
| `listenerOptions` | `{ passive: boolean; }` | const | `{ passive: true }` | ✗ |
| `shouldListen` | `boolean` | let/var | `true` | ✗ |
| `vm` | `ComponentPublicInstance` | const | `toValue(target) as ComponentPublicInstance` | ✗ |
| `vm` | `ComponentPublicInstance` | const | `toValue(target) as ComponentPublicInstance` | ✗ |
| `children` | `any` | const | `vm.$.subTree && vm.$.subTree.children` | ✗ |
| `isProcessingClick` | `boolean` | let/var | `false` | ✗ |
| `cleanup` | `Fn[]` | const | `[
    useEventListener(window, 'click', (event: PointerEvent) => {
      if (!isProcessingClick) {
        isProcessingClick = true
        setTimeout(() => {
          isProcessingClick = false
        }, 0)
        listener(event)
      }
    }, { passive: true, capture }),
    useEventListener(window, 'pointerdown', (e) => {
      const el = unrefElement(target)
      shouldListen = !shouldIgnore(e) && !!(el && !e.composedPath().includes(el))
    }, { passive: true }),
    detectIframe && useEventListener(window, 'blur', (event) => {
      setTimeout(() => {
        const el = unrefElement(target)
        if (
          window.document.activeElement?.tagName === 'IFRAME'
          && !el?.contains(window.document.activeElement)
        ) {
          handler(event as any)
        }
      }, 0)
    }, { passive: true }),
  ].filter(Boolean) as Fn[]` | ✗ |


---

## Functions

### `onClickOutside(target: MaybeElementRef, handler: OnClickOutsideHandler<{ detectIframe: OnClickOutsideOptions['detectIframe'], controls: true }>, options: OnClickOutsideOptions<true>): { stop: Fn, cancel: Fn, trigger: (event: Event) => void }`

<details><summary>Code</summary>

```ts
export function onClickOutside(
  target: MaybeElementRef,
  handler: OnClickOutsideHandler<{ detectIframe: OnClickOutsideOptions['detectIframe'], controls: true }>,
  options: OnClickOutsideOptions<true>,
): { stop: Fn, cancel: Fn, trigger: (event: Event) => void }
```
</details>

- **JSDoc**:
```ts
/**
 * Listen for clicks outside of an element.
 *
 * @see https://vueuse.org/onClickOutside
 * @param target
 * @param handler
 * @param options
 */
```

- **Parameters**:
  - `target: MaybeElementRef`
  - `handler: OnClickOutsideHandler<{ detectIframe: OnClickOutsideOptions['detectIframe'], controls: true }>`
  - `options: OnClickOutsideOptions<true>`
- **Return Type**: `{ stop: Fn, cancel: Fn, trigger: (event: Event) => void }`
### `shouldIgnore(event: Event): any`

<details><summary>Code</summary>

```ts
(event: Event) => {
    return toValue(ignore).some((target) => {
      if (typeof target === 'string') {
        return Array.from(window.document.querySelectorAll(target))
          .some(el => el === event.target || event.composedPath().includes(el))
      }
      else {
        const el = unrefElement(target)
        return el && (event.target === el || event.composedPath().includes(el))
      }
    })
  }
```
</details>

- **Parameters**:
  - `event: Event`
- **Return Type**: `any`
- **Calls**:
  - `toValue(ignore).some`
  - `Array.from(window.document.querySelectorAll(target))
          .some`
  - `event.composedPath().includes`
  - `unrefElement (from ../unrefElement)`
### `hasMultipleRoots(target: MaybeElementRef): boolean`

<details><summary>Code</summary>

```ts
function hasMultipleRoots(target: MaybeElementRef): boolean {
    const vm = toValue(target) as ComponentPublicInstance
    return vm && vm.$.subTree.shapeFlag === 16
  }
```
</details>

- **JSDoc**:
```ts
/**
   * Determines if the given target has multiple root elements.
   * Referenced from: https://github.com/vuejs/test-utils/blob/ccb460be55f9f6be05ab708500a41ec8adf6f4bc/src/vue-wrapper.ts#L21
   */
```

- **Parameters**:
  - `target: MaybeElementRef`
- **Return Type**: `boolean`
- **Calls**:
  - `toValue (from vue)`
### `checkMultipleRoots(target: MaybeElementRef, event: Event): boolean`

<details><summary>Code</summary>

```ts
function checkMultipleRoots(target: MaybeElementRef, event: Event): boolean {
    const vm = toValue(target) as ComponentPublicInstance
    const children = vm.$.subTree && vm.$.subTree.children

    if (children == null || !Array.isArray(children))
      return false

    // @ts-expect-error should be VNode
    return children.some((child: VNode) => child.el === event.target || event.composedPath().includes(child.el))
  }
```
</details>

- **Parameters**:
  - `target: MaybeElementRef`
  - `event: Event`
- **Return Type**: `boolean`
- **Calls**:
  - `toValue (from vue)`
  - `Array.isArray`
  - `children.some`
  - `event.composedPath().includes`
- **Internal Comments**:
```
// @ts-expect-error should be VNode
```

### `listener(event: Event): void`

<details><summary>Code</summary>

```ts
(event: Event) => {
    const el = unrefElement(target)

    if (event.target == null)
      return

    if (!(el instanceof Element) && hasMultipleRoots(target) && checkMultipleRoots(target, event))
      return

    if (!el || el === event.target || event.composedPath().includes(el))
      return

    if ('detail' in event && event.detail === 0)
      shouldListen = !shouldIgnore(event)

    if (!shouldListen) {
      shouldListen = true
      return
    }

    handler(event as any)
  }
```
</details>

- **Parameters**:
  - `event: Event`
- **Return Type**: `void`
- **Calls**:
  - `unrefElement (from ../unrefElement)`
  - `hasMultipleRoots`
  - `checkMultipleRoots`
  - `event.composedPath().includes`
  - `shouldIgnore`
  - `handler`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => cleanup.forEach(fn => fn())
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `cleanup.forEach`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => {
        shouldListen = false
      }
```
</details>

- **Return Type**: `void`
### `trigger(event: Event): void`

<details><summary>Code</summary>

```ts
(event: Event) => {
        shouldListen = true
        listener(event)
        shouldListen = false
      }
```
</details>

- **Parameters**:
  - `event: Event`
- **Return Type**: `void`
- **Calls**:
  - `listener`
### `cancel(): void`

<details><summary>Code</summary>

```ts
() => {
        shouldListen = false
      }
```
</details>

- **Return Type**: `void`
### `trigger(event: Event): void`

<details><summary>Code</summary>

```ts
(event: Event) => {
        shouldListen = true
        listener(event)
        shouldListen = false
      }
```
</details>

- **Parameters**:
  - `event: Event`
- **Return Type**: `void`
- **Calls**:
  - `listener`

---

## Interfaces

### `OnClickOutsideOptions<Controls extends boolean = false>`

<details><summary>Interface Code</summary>

```ts
export interface OnClickOutsideOptions<Controls extends boolean = false> extends ConfigurableWindow {
  /**
   * List of elements that should not trigger the event.
   */
  ignore?: MaybeRefOrGetter<(MaybeElementRef | string)[]>
  /**
   * Use capturing phase for internal event listener.
   * @default true
   */
  capture?: boolean
  /**
   * Run handler function if focus moves to an iframe.
   * @default false
   */
  detectIframe?: boolean
  /**
   * Use controls to cancel/trigger listener.
   * @default false
   */
  controls?: Controls
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `ignore` | `MaybeRefOrGetter<(MaybeElementRef | string)[]>` | ✓ |  |
| `capture` | `boolean` | ✓ |  |
| `detectIframe` | `boolean` | ✓ |  |
| `controls` | `Controls` | ✓ |  |


---

## Type Aliases

### `OnClickOutsideHandler<T extends {
    detectIframe: OnClickOutsideOptions['detectIframe']
    controls: boolean
  } = { detectIframe: false, controls: false } extends {
    detectIframe: OnClickOutsideOptions['detectIframe']
    controls: boolean
  } = { detectIframe: false, controls: false }>`

```ts
type OnClickOutsideHandler<T extends {
    detectIframe: OnClickOutsideOptions['detectIframe']
    controls: boolean
  } = { detectIframe: false, controls: false } extends {
    detectIframe: OnClickOutsideOptions['detectIframe']
    controls: boolean
  } = { detectIframe: false, controls: false }> = (
  event: T['controls'] extends true ? Event | (T['detectIframe'] extends true
    ? PointerEvent | FocusEvent
    : PointerEvent) : T['detectIframe'] extends true
    ? PointerEvent | FocusEvent
    : PointerEvent,
) => void;
```


---