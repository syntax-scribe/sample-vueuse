[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 10
- **Classes**: 0
- **Imports**: 13
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/integrations/useSortable/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ConfigurableDocument` | `@vueuse/core` |
| `MaybeElement` | `@vueuse/core` |
| `Options` | `sortablejs` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `defaultDocument` | `@vueuse/core` |
| `tryOnMounted` | `@vueuse/core` |
| `tryOnScopeDispose` | `@vueuse/core` |
| `unrefElement` | `@vueuse/core` |
| `Sortable` | `sortablejs` |
| `isRef` | `vue` |
| `nextTick` | `vue` |
| `toValue` | `vue` |


---

## Functions

### `useSortable(selector: string, list: MaybeRefOrGetter<T[]>, options: UseSortableOptions): UseSortableReturn`

<details><summary>Code</summary>

```ts
export function useSortable<T>(selector: string, list: MaybeRefOrGetter<T[]>,
  options?: UseSortableOptions): UseSortableReturn
```
</details>

- **Parameters**:
  - `selector: string`
  - `list: MaybeRefOrGetter<T[]>`
  - `options: UseSortableOptions`
- **Return Type**: `UseSortableReturn`
### `onUpdate(e: any): void`

<details><summary>Code</summary>

```ts
(e) => {
      moveArrayElement(list, e.oldIndex!, e.newIndex!, e)
    }
```
</details>

- **Parameters**:
  - `e: any`
- **Return Type**: `void`
- **Calls**:
  - `moveArrayElement`
### `onUpdate(e: any): void`

<details><summary>Code</summary>

```ts
(e) => {
      moveArrayElement(list, e.oldIndex!, e.newIndex!, e)
    }
```
</details>

- **Parameters**:
  - `e: any`
- **Return Type**: `void`
- **Calls**:
  - `moveArrayElement`
### `onUpdate(e: any): void`

<details><summary>Code</summary>

```ts
(e) => {
      moveArrayElement(list, e.oldIndex!, e.newIndex!, e)
    }
```
</details>

- **Parameters**:
  - `e: any`
- **Return Type**: `void`
- **Calls**:
  - `moveArrayElement`
### `start(): void`

<details><summary>Code</summary>

```ts
() => {
    const target = (typeof el === 'string' ? document?.querySelector(el) : unrefElement(el))
    if (!target || sortable !== undefined)
      return
    sortable = new Sortable(target as HTMLElement, { ...defaultOptions, ...resetOptions })
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `document?.querySelector`
  - `unrefElement (from @vueuse/core)`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    sortable?.destroy()
    sortable = undefined
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `sortable?.destroy`
### `option(name: K, value: Options[K]): any`

<details><summary>Code</summary>

```ts
<K extends keyof Options>(name: K, value?: Options[K]) => {
    if (value !== undefined)
      sortable?.option(name, value)
    else
      return sortable?.option(name)
  }
```
</details>

- **Parameters**:
  - `name: K`
  - `value: Options[K]`
- **Return Type**: `any`
- **Calls**:
  - `sortable?.option`
### `insertNodeAt(parentElement: Element, element: Element, index: number): void`

<details><summary>Code</summary>

```ts
export function insertNodeAt(
  parentElement: Element,
  element: Element,
  index: number,
) {
  const refElement = parentElement.children[index]
  parentElement.insertBefore(element, refElement)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Inserts a element into the DOM at a given index.
 * @param parentElement
 * @param element
 * @param {number} index
 * @see https://github.com/Alfred-Skyblue/vue-draggable-plus/blob/a3829222095e1949bf2c9a20979d7b5930e66f14/src/utils/index.ts#L81C1-L94C2
 */
```

- **Parameters**:
  - `parentElement: Element`
  - `element: Element`
  - `index: number`
- **Return Type**: `void`
- **Calls**:
  - `parentElement.insertBefore`
### `removeNode(node: Node): void`

<details><summary>Code</summary>

```ts
export function removeNode(node: Node) {
  if (node.parentNode)
    node.parentNode.removeChild(node)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Removes a node from the DOM.
 * @param {Node} node
 * @see https://github.com/Alfred-Skyblue/vue-draggable-plus/blob/a3829222095e1949bf2c9a20979d7b5930e66f14/src/utils/index.ts#L96C1-L102C2
 */
```

- **Parameters**:
  - `node: Node`
- **Return Type**: `void`
- **Calls**:
  - `node.parentNode.removeChild`
### `moveArrayElement(list: MaybeRefOrGetter<T[]>, from: number, to: number, e: Sortable.SortableEvent | null): void`

<details><summary>Code</summary>

```ts
export function moveArrayElement<T>(
  list: MaybeRefOrGetter<T[]>,
  from: number,
  to: number,
  e: Sortable.SortableEvent | null = null,
): void {
  if (e != null) {
    removeNode(e.item)
    insertNodeAt(e.from, e.item, from)
  }

  const _valueIsRef = isRef(list)
  // When the list is a ref, make a shallow copy of it to avoid repeatedly triggering side effects when moving elements
  const array = _valueIsRef ? [...toValue(list)] : toValue(list)

  if (to >= 0 && to < array.length) {
    const element = array.splice(from, 1)[0]
    nextTick(() => {
      array.splice(to, 0, element)
      // When list is ref, assign array to list.value
      if (_valueIsRef)
        (list as MaybeRef).value = array
    })
  }
}
```
</details>

- **Parameters**:
  - `list: MaybeRefOrGetter<T[]>`
  - `from: number`
  - `to: number`
  - `e: Sortable.SortableEvent | null`
- **Return Type**: `void`
- **Calls**:
  - `removeNode`
  - `insertNodeAt`
  - `isRef (from vue)`
  - `toValue (from vue)`
  - `array.splice`
  - `nextTick (from vue)`
- **Internal Comments**:
```
// When the list is a ref, make a shallow copy of it to avoid repeatedly triggering side effects when moving elements (x2)
// When list is ref, assign array to list.value
```


---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseSortableReturn`

<details><summary>Interface Code</summary>

```ts
export interface UseSortableReturn {
  /**
   * start sortable instance
   */
  start: () => void
  /**
   * destroy sortable instance
   */
  stop: () => void

  /**
   * Options getter/setter
   * @param name a Sortable.Options property.
   * @param value a value.
   */
  option: (<K extends keyof Sortable.Options>(name: K, value: Sortable.Options[K]) => void) & (<K extends keyof Sortable.Options>(name: K) => Sortable.Options[K])
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `start` | `() => void` | ✗ |  |
| `stop` | `() => void` | ✗ |  |
| `option` | `(<K extends keyof Sortable.Options>(name: K, value: Sortable.Options[K]) => void) & (<K extends keyof Sortable.Options>(name: K) => Sortable.Options[K])` | ✗ |  |


---

## Type Aliases

### `UseSortableOptions`

```ts
type UseSortableOptions = Options & ConfigurableDocument;
```


---