[⬅️ Back to Table of Contents](../../index.md)

# 📄 `mount.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 4 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 1 |
| 📑 Type Aliases | 2 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/.test/mount.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `InjectionKey` | `vue` |
| `Ref` | `vue` |
| `createApp` | `vue` |
| `defineComponent` | `vue` |
| `h` | `vue` |
| `provide` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `comp` | `VM<V>` | const | `app.mount(el) as any as VM<V>` | ✗ |


---

## Functions

### `mount(Comp: V): VM<V>`

<details><summary>Code</summary>

```ts
export function mount<V>(Comp: V) {
  const el = document.createElement('div')
  const app = createApp(Comp as any)

  const unmount = () => app.unmount()
  const comp = app.mount(el) as any as VM<V>
  comp.unmount = unmount
  return comp
}
```
</details>

- **Parameters**:
  - `Comp: V`
- **Return Type**: `VM<V>`
- **Calls**:
  - `document.createElement`
  - `createApp (from vue)`
  - `app.unmount`
  - `app.mount`
### `unmount(): any`

<details><summary>Code</summary>

```ts
() => app.unmount()
```
</details>

- **Return Type**: `any`
- **Calls**:
  - `app.unmount`
### `useSetup(setup: () => V): any`

<details><summary>Code</summary>

```ts
export function useSetup<V>(setup: () => V) {
  const Comp = defineComponent({
    setup,
    render() {
      return h('div', [])
    },
  })

  return mount(Comp)
}
```
</details>

- **Parameters**:
  - `setup: () => V`
- **Return Type**: `any`
- **Calls**:
  - `defineComponent (from vue)`
  - `h (from vue)`
  - `mount`
### `useInjectedSetup(setup: () => V): any`

<details><summary>Code</summary>

```ts
export function useInjectedSetup<V>(setup: () => V) {
  const Comp = defineComponent({
    setup,
    render() {
      return h('div', [])
    },
  })

  const Provider = defineComponent({
    components: Comp,
    setup() {
      provide(Key, shallowRef(1))
    },
    render() {
      return h('div', [])
    },
  })

  return mount(Provider)
}
```
</details>

- **Parameters**:
  - `setup: () => V`
- **Return Type**: `any`
- **Calls**:
  - `defineComponent (from vue)`
  - `h (from vue)`
  - `provide (from vue)`
  - `shallowRef (from vue)`
  - `mount`

---

## Type Aliases

### `InstanceType<V>`

```ts
type InstanceType<V> = V extends { new (...arg: any[]): infer X } ? X : never;
```

### `VM<V>`

```ts
type VM<V> = InstanceType<V> & { unmount: () => void };
```


---