[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 8
- **Classes**: 0
- **Imports**: 9
- **Interfaces**: 2
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/createTemplatePromise/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `DefineComponent` | `vue` |
| `Ref` | `vue` |
| `TransitionGroupProps` | `vue` |
| `deepRef` | `vue` |
| `defineComponent` | `vue` |
| `Fragment` | `vue` |
| `h` | `vue` |
| `shallowReactive` | `vue` |
| `TransitionGroup` | `vue` |


---

## Functions

### `createTemplatePromise(options: TemplatePromiseOptions): TemplatePromise<Return, Args>`

<details><summary>Code</summary>

```ts
export function createTemplatePromise<Return, Args extends any[] = []>(
  options: TemplatePromiseOptions = {},
): TemplatePromise<Return, Args> {
  let index = 0
  const instances = deepRef([]) as Ref<TemplatePromiseProps<Return, Args>[]>

  function create(...args: Args) {
    const props = shallowReactive({
      key: index++,
      args,
      promise: undefined,
      resolve: () => {},
      reject: () => {},
      isResolving: false,
      options,
    }) as TemplatePromiseProps<Return, Args>

    instances.value.push(props)

    props.promise = new Promise<Return>((_resolve, _reject) => {
      props.resolve = (v) => {
        props.isResolving = true
        return _resolve(v)
      }
      props.reject = _reject
    })
      .finally(() => {
        props.promise = undefined
        const index = instances.value.indexOf(props)
        if (index !== -1)
          instances.value.splice(index, 1)
      })

    return props.promise
  }

  function start(...args: Args) {
    if (options.singleton && instances.value.length > 0)
      return instances.value[0].promise
    return create(...args)
  }

  const component = defineComponent((_, { slots }) => {
    const renderList = () => instances.value.map(props => h(Fragment, { key: props.key }, slots.default?.(props)))
    if (options.transition)
      return () => h(TransitionGroup, options.transition, renderList)
    return renderList
  })

  // @ts-expect-error There's a breaking type change in Vue 3.3 <https://github.com/vuejs/core/pull/7963>
  component.start = start

  return component as any
}
```
</details>

- **JSDoc**:
```ts
/**
 * Creates a template promise component.
 *
 * @see https://vueuse.org/createTemplatePromise
 */
```

- **Parameters**:
  - `options: TemplatePromiseOptions`
- **Return Type**: `TemplatePromise<Return, Args>`
- **Calls**:
  - `deepRef (from vue)`
  - `shallowReactive (from vue)`
  - `instances.value.push`
  - `new Promise<Return>((_resolve, _reject) => {
      props.resolve = (v) => {
        props.isResolving = true
        return _resolve(v)
      }
      props.reject = _reject
    })
      .finally`
  - `_resolve`
  - `instances.value.indexOf`
  - `instances.value.splice`
  - `create`
  - `defineComponent (from vue)`
  - `instances.value.map`
  - `h (from vue)`
  - `slots.default`
- **Internal Comments**:
```
// @ts-expect-error There's a breaking type change in Vue 3.3 <https://github.com/vuejs/core/pull/7963> (x4)
```

### `create(args: Args): Promise<Return>`

<details><summary>Code</summary>

```ts
function create(...args: Args) {
    const props = shallowReactive({
      key: index++,
      args,
      promise: undefined,
      resolve: () => {},
      reject: () => {},
      isResolving: false,
      options,
    }) as TemplatePromiseProps<Return, Args>

    instances.value.push(props)

    props.promise = new Promise<Return>((_resolve, _reject) => {
      props.resolve = (v) => {
        props.isResolving = true
        return _resolve(v)
      }
      props.reject = _reject
    })
      .finally(() => {
        props.promise = undefined
        const index = instances.value.indexOf(props)
        if (index !== -1)
          instances.value.splice(index, 1)
      })

    return props.promise
  }
```
</details>

- **Parameters**:
  - `args: Args`
- **Return Type**: `Promise<Return>`
- **Calls**:
  - `shallowReactive (from vue)`
  - `instances.value.push`
  - `new Promise<Return>((_resolve, _reject) => {
      props.resolve = (v) => {
        props.isResolving = true
        return _resolve(v)
      }
      props.reject = _reject
    })
      .finally`
  - `_resolve`
  - `instances.value.indexOf`
  - `instances.value.splice`
### `resolve(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`
### `reject(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`
### `resolve(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`
### `reject(): void`

<details><summary>Code</summary>

```ts
() => {}
```
</details>

- **Return Type**: `void`
### `start(args: Args): any`

<details><summary>Code</summary>

```ts
function start(...args: Args) {
    if (options.singleton && instances.value.length > 0)
      return instances.value[0].promise
    return create(...args)
  }
```
</details>

- **Parameters**:
  - `args: Args`
- **Return Type**: `any`
- **Calls**:
  - `create`
### `renderList(): any`

<details><summary>Code</summary>

```ts
() => instances.value.map(props => h(Fragment, { key: props.key }, slots.default?.(props)))
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `instances.value.map`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `TemplatePromiseProps<Return, Args extends any[] = []>`

<details><summary>Interface Code</summary>

```ts
export interface TemplatePromiseProps<Return, Args extends any[] = []> {
  /**
   * The promise instance.
   */
  promise: Promise<Return> | undefined
  /**
   * Resolve the promise.
   */
  resolve: (v: Return | Promise<Return>) => void
  /**
   * Reject the promise.
   */
  reject: (v: any) => void
  /**
   * Arguments passed to TemplatePromise.start()
   */
  args: Args
  /**
   * Indicates if the promise is resolving.
   * When passing another promise to `resolve`, this will be set to `true` until the promise is resolved.
   */
  isResolving: boolean
  /**
   * Options passed to createTemplatePromise()
   */
  options: TemplatePromiseOptions
  /**
   * Unique key for list rendering.
   */
  key: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `promise` | `Promise<Return> | undefined` | ✗ |  |
| `resolve` | `(v: Return | Promise<Return>) => void` | ✗ |  |
| `reject` | `(v: any) => void` | ✗ |  |
| `args` | `Args` | ✗ |  |
| `isResolving` | `boolean` | ✗ |  |
| `options` | `TemplatePromiseOptions` | ✗ |  |
| `key` | `number` | ✗ |  |

### `TemplatePromiseOptions`

<details><summary>Interface Code</summary>

```ts
export interface TemplatePromiseOptions {
  /**
   * Determines if the promise can be called only once at a time.
   *
   * @default false
   */
  singleton?: boolean

  /**
   * Transition props for the promise.
   */
  transition?: TransitionGroupProps
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `singleton` | `boolean` | ✓ |  |
| `transition` | `TransitionGroupProps` | ✓ |  |


---

## Type Aliases

### `TemplatePromise<Return, Args extends any[] = [] extends any[] = []>`

```ts
type TemplatePromise<Return, Args extends any[] = [] extends any[] = []> = DefineComponent<object> & {
  new(): {
    $slots: {
      default: (_: TemplatePromiseProps<Return, Args>) => any
    }
  }
} & {
  start: (...args: Args) => Promise<Return>
};
```


---