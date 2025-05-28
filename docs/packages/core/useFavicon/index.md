[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 0 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 1 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Vue Composition API](#vue-composition-api)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/core/useFavicon/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `ReadonlyRefOrGetter` | `@vueuse/shared` |
| `ComputedRef` | `vue` |
| `MaybeRef` | `vue` |
| `MaybeRefOrGetter` | `vue` |
| `Ref` | `vue` |
| `ConfigurableDocument` | `../_configurable` |
| `toRef` | `@vueuse/shared` |
| `watch` | `vue` |
| `defaultDocument` | `../_configurable` |


---

## Vue Composition API

| Name | Type | Reactive Variables | Composables |
|------|------|-------------------|-------------|
| `watch` | watch | *none* | *none* |


---

## Functions

### `useFavicon(newIcon: ReadonlyRefOrGetter<string | null | undefined>, options: UseFaviconOptions): ComputedRef<string | null | undefined>`

<details><summary>Code</summary>

```ts
export function useFavicon(
  newIcon: ReadonlyRefOrGetter<string | null | undefined>,
  options?: UseFaviconOptions
): ComputedRef<string | null | undefined>
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive favicon.
 *
 * @see https://vueuse.org/useFavicon
 * @param newIcon
 * @param options
 */
```

- **Parameters**:
  - `newIcon: ReadonlyRefOrGetter<string | null | undefined>`
  - `options: UseFaviconOptions`
- **Return Type**: `ComputedRef<string | null | undefined>`
### `applyIcon(icon: string): void`

<details><summary>Code</summary>

```ts
(icon: string) => {
    const elements = document?.head
      .querySelectorAll<HTMLLinkElement>(`link[rel*="${rel}"]`)
    if (!elements || elements.length === 0) {
      const link = document?.createElement('link')
      if (link) {
        link.rel = rel
        link.href = `${baseUrl}${icon}`
        link.type = `image/${icon.split('.').pop()}`
        document?.head.append(link)
      }
      return
    }
    elements?.forEach(el => el.href = `${baseUrl}${icon}`)
  }
```
</details>

- **Parameters**:
  - `icon: string`
- **Return Type**: `void`
- **Calls**:
  - `document?.head
      .querySelectorAll`
  - `document?.createElement`
  - `icon.split('.').pop`
  - `document?.head.append`
  - `elements?.forEach`

---

## Interfaces

### `UseFaviconOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseFaviconOptions extends ConfigurableDocument {
  baseUrl?: string
  rel?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `baseUrl` | `string` | ✓ |  |
| `rel` | `string` | ✓ |  |


---

## Type Aliases

### `UseFaviconReturn`

```ts
type UseFaviconReturn = ReturnType<typeof useFavicon>;
```


---