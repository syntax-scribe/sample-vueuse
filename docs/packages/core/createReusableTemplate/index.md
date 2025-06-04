[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 3 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 5 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/createReusableTemplate/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ComponentObjectPropsOptions` | `vue` |
| `DefineComponent` | `vue` |
| `Slot` | `vue` |
| `camelize` | `@vueuse/shared` |
| `makeDestructurable` | `@vueuse/shared` |
| `defineComponent` | `vue` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `define` | `any` | const | `defineComponent({
    setup(_, { slots }) {
      return () => {
        render.value = slots.default
      }
    },
  }) as unknown as DefineTemplateComponent<Bindings, MapSlotNameToSlotProps>` | ✗ |
| `reuse` | `any` | const | `defineComponent({
    inheritAttrs,
    props: options.props,
    setup(props, { attrs, slots }) {
      return () => {
        if (!render.value && process.env.NODE_ENV !== 'production')
          throw new Error('[VueUse] Failed to find the definition of reusable template')
        const vnode = render.value?.({
          ...(options.props == null
            ? keysToCamelKebabCase(attrs)
            : props),
          $slots: slots,
        })

        return (inheritAttrs && vnode?.length === 1) ? vnode[0] : vnode
      }
    },
  }) as unknown as ReuseTemplateComponent<Bindings, MapSlotNameToSlotProps>` | ✗ |
| `newObj` | `typeof obj` | const | `{}` | ✗ |


---

## Functions

### `createReusableTemplate(options: CreateReusableTemplateOptions<Bindings>): ReusableTemplatePair<Bindings, MapSlotNameToSlotProps>`

<details><summary>Code</summary>

```ts
export function createReusableTemplate<
  Bindings extends Record<string, any>,
  MapSlotNameToSlotProps extends ObjectLiteralWithPotentialObjectLiterals = Record<'default', undefined>,
>(
  options: CreateReusableTemplateOptions<Bindings> = {},
): ReusableTemplatePair<Bindings, MapSlotNameToSlotProps> {
  const {
    inheritAttrs = true,
  } = options

  const render = shallowRef<Slot | undefined>()

  const define = defineComponent({
    setup(_, { slots }) {
      return () => {
        render.value = slots.default
      }
    },
  }) as unknown as DefineTemplateComponent<Bindings, MapSlotNameToSlotProps>

  const reuse = defineComponent({
    inheritAttrs,
    props: options.props,
    setup(props, { attrs, slots }) {
      return () => {
        if (!render.value && process.env.NODE_ENV !== 'production')
          throw new Error('[VueUse] Failed to find the definition of reusable template')
        const vnode = render.value?.({
          ...(options.props == null
            ? keysToCamelKebabCase(attrs)
            : props),
          $slots: slots,
        })

        return (inheritAttrs && vnode?.length === 1) ? vnode[0] : vnode
      }
    },
  }) as unknown as ReuseTemplateComponent<Bindings, MapSlotNameToSlotProps>

  return makeDestructurable(
    { define, reuse },
    [define, reuse],
  ) as any
}
```
</details>

- **JSDoc**:
```ts
/**
 * This function creates `define` and `reuse` components in pair,
 * It also allow to pass a generic to bind with type.
 *
 * @see https://vueuse.org/createReusableTemplate
 */
```

- **Parameters**:
  - `options: CreateReusableTemplateOptions<Bindings>`
- **Return Type**: `ReusableTemplatePair<Bindings, MapSlotNameToSlotProps>`
- **Calls**:
  - `shallowRef (from vue)`
  - `defineComponent (from vue)`
  - `render.value`
  - `keysToCamelKebabCase`
  - `makeDestructurable (from @vueuse/shared)`
### `keysToCamelKebabCase(obj: Record<string, any>): Record<string, any>`

<details><summary>Code</summary>

```ts
function keysToCamelKebabCase(obj: Record<string, any>) {
  const newObj: typeof obj = {}
  for (const key in obj)
    newObj[camelize(key)] = obj[key]
  return newObj
}
```
</details>

- **Parameters**:
  - `obj: Record<string, any>`
- **Return Type**: `Record<string, any>`
- **Calls**:
  - `camelize (from @vueuse/shared)`

---

## Interfaces

### `CreateReusableTemplateOptions<Props extends Record<string, any>>`

<details><summary>Interface Code</summary>

```ts
export interface CreateReusableTemplateOptions<Props extends Record<string, any>> {
  /**
   * Inherit attrs from reuse component.
   *
   * @default true
   */
  inheritAttrs?: boolean
  /**
   * Props definition for reuse component.
   */
  props?: ComponentObjectPropsOptions<Props>
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `inheritAttrs` | `boolean` | ✓ |  |
| `props` | `ComponentObjectPropsOptions<Props>` | ✓ |  |


---

## Type Aliases

### `ObjectLiteralWithPotentialObjectLiterals`

```ts
type ObjectLiteralWithPotentialObjectLiterals = Record<string, Record<string, any> | undefined>;
```

### `GenerateSlotsFromSlotMap<T extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals>`

```ts
type GenerateSlotsFromSlotMap<T extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals> = {
  [K in keyof T]: Slot<T[K]>
};
```

### `DefineTemplateComponent<Bindings extends Record<string, any> extends Record<string, any>, MapSlotNameToSlotProps extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals>`

```ts
type DefineTemplateComponent<Bindings extends Record<string, any> extends Record<string, any>, MapSlotNameToSlotProps extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals> = DefineComponent & {
  new(): { $slots: { default: (_: Bindings & { $slots: GenerateSlotsFromSlotMap<MapSlotNameToSlotProps> }) => any } }
};
```

### `ReuseTemplateComponent<Bindings extends Record<string, any> extends Record<string, any>, MapSlotNameToSlotProps extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals>`

```ts
type ReuseTemplateComponent<Bindings extends Record<string, any> extends Record<string, any>, MapSlotNameToSlotProps extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals> = DefineComponent<Bindings> & {
  new(): { $slots: GenerateSlotsFromSlotMap<MapSlotNameToSlotProps> }
};
```

### `ReusableTemplatePair<Bindings extends Record<string, any> extends Record<string, any>, MapSlotNameToSlotProps extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals>`

```ts
type ReusableTemplatePair<Bindings extends Record<string, any> extends Record<string, any>, MapSlotNameToSlotProps extends ObjectLiteralWithPotentialObjectLiterals extends ObjectLiteralWithPotentialObjectLiterals> = [
  DefineTemplateComponent<Bindings, MapSlotNameToSlotProps>,
  ReuseTemplateComponent<Bindings, MapSlotNameToSlotProps>,
] & {
  define: DefineTemplateComponent<Bindings, MapSlotNameToSlotProps>
  reuse: ReuseTemplateComponent<Bindings, MapSlotNameToSlotProps>
};
```


---