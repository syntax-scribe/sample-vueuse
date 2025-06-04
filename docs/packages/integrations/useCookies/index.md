[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 16 |
| 📦 Imports | 4 |
| 📊 Variables & Constants | 2 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/integrations/useCookies/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `IncomingMessage` | `node:http` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `Cookie` | `universal-cookie` |
| `shallowRef` | `vue` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `universalCookie` | `any` | const | `new Cookie(req ? req.headers.cookie : null)` | ✗ |
| `watchingDependencies` | `string[]` | const | `autoUpdateDependencies ? [...dependencies || []] : dependencies` | ✗ |


---

## Functions

### `createCookies(req: IncomingMessage): (dependencies?: string[], { doNotParse, autoUpdateDependencies }?: { doNotParse?: boolean; autoUpdateDependencies?: boolean; }) => { get: <T = any>(...args: unknown[]) => any; getAll: <T = any>(...args: unknown[]) => any; set: (...args: unknown[]) => any; remove: (...args: unknown[]) => any; addChangeListener: (...a...`

<details><summary>Code</summary>

```ts
export function createCookies(req?: IncomingMessage) {
  const universalCookie = new Cookie(req ? req.headers.cookie : null)

  return (
    dependencies?: string[] | null,
    { doNotParse = false, autoUpdateDependencies = false } = {},
  ) => useCookies(dependencies, { doNotParse, autoUpdateDependencies }, universalCookie)
}
```
</details>

- **JSDoc**:
```ts
/**
 * Creates a new {@link useCookies} function
 * @param req - incoming http request (for SSR)
 * @see https://github.com/reactivestack/cookies/tree/master/packages/universal-cookie universal-cookie
 * @description Creates universal-cookie instance using request (default is window.document.cookie) and returns {@link useCookies} function with provided universal-cookie instance
 */
```

- **Parameters**:
  - `req: IncomingMessage`
- **Return Type**: `(dependencies?: string[], { doNotParse, autoUpdateDependencies }?: { doNotParse?: boolean; autoUpdateDependencies?: boolean; }) => { get: <T = any>(...args: unknown[]) => any; getAll: <T = any>(...args: unknown[]) => any; set: (...args: unknown[]) => any; remove: (...args: unknown[]) => any; addChangeListener: (...a...`
- **Calls**:
  - `useCookies`
### `useCookies(dependencies: string[] | null, { doNotParse = false, autoUpdateDependencies = false }: any, cookies: any): { get: <T = any>(...args: unknown[]) => any; getAll: <T = any>(...args: unknown[]) => any; set: (...args: unknown[]) => any; remove: (...args: unknown[]) => any; addChangeListener: (...args: unknown[]) => any; removeChangeListener: (...args: unknown[]) => any; }`

<details><summary>Code</summary>

```ts
export function useCookies(
  dependencies?: string[] | null,
  { doNotParse = false, autoUpdateDependencies = false } = {},
  cookies = new Cookie(),
) {
  const watchingDependencies = autoUpdateDependencies ? [...dependencies || []] : dependencies

  let previousCookies = cookies.getAll<RawCookies>({ doNotParse: true })

  /**
   * Adds reactivity to get/getAll methods
   */
  const touches = shallowRef(0)

  const onChange = () => {
    const newCookies = cookies.getAll({ doNotParse: true })

    if (
      shouldUpdate(
        watchingDependencies || null,
        newCookies,
        previousCookies,
      )
    ) {
      touches.value++
    }

    previousCookies = newCookies
  }

  cookies.addChangeListener(onChange)

  tryOnScopeDispose(() => {
    cookies.removeChangeListener(onChange)
  })

  return {
    /**
     * Reactive get cookie by name. If **autoUpdateDependencies = true** then it will update watching dependencies
     */
    get: <T = any>(...args: Parameters<Cookie['get']>) => {
      /**
       * Auto update watching dependencies if needed
       */
      if (autoUpdateDependencies && watchingDependencies && !watchingDependencies.includes(args[0]))
        watchingDependencies.push(args[0])

      // eslint-disable-next-line ts/no-unused-expressions
      touches.value // adds reactivity to method
      return cookies.get<T>(args[0], { doNotParse, ...args[1] })
    },
    /**
     * Reactive get all cookies
     */
    getAll: <T = any>(...args: Parameters<Cookie['getAll']>) => {
      // eslint-disable-next-line ts/no-unused-expressions
      touches.value // adds reactivity to method
      return cookies.getAll<T>({ doNotParse, ...args[0] })
    },
    set: (...args: Parameters<Cookie['set']>) => cookies.set(...args),
    remove: (...args: Parameters<Cookie['remove']>) => cookies.remove(...args),
    addChangeListener: (...args: Parameters<Cookie['addChangeListener']>) => cookies.addChangeListener(...args),
    removeChangeListener: (...args: Parameters<Cookie['removeChangeListener']>) => cookies.removeChangeListener(...args),
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive methods to work with cookies (use {@link createCookies} method instead if you are using SSR)
 * @param dependencies - array of watching cookie's names. Pass empty array if don't want to watch cookies changes.
 * @param options
 * @param options.doNotParse - don't try parse value as JSON
 * @param options.autoUpdateDependencies - automatically update watching dependencies
 * @param cookies - universal-cookie instance
 */
```

- **Parameters**:
  - `dependencies: string[] | null`
  - `{ doNotParse = false, autoUpdateDependencies = false }: any`
  - `cookies: any`
- **Return Type**: `{ get: <T = any>(...args: unknown[]) => any; getAll: <T = any>(...args: unknown[]) => any; set: (...args: unknown[]) => any; remove: (...args: unknown[]) => any; addChangeListener: (...args: unknown[]) => any; removeChangeListener: (...args: unknown[]) => any; }`
- **Calls**:
  - `cookies.getAll`
  - `shallowRef (from vue)`
  - `shouldUpdate`
  - `cookies.addChangeListener`
  - `tryOnScopeDispose (from @vueuse/shared)`
  - `cookies.removeChangeListener`
  - `watchingDependencies.includes`
  - `watchingDependencies.push`
  - `cookies.get`
  - `cookies.set`
  - `cookies.remove`
- **Internal Comments**:
```
/**
   * Adds reactivity to get/getAll methods
   */ (x2)
/**
     * Reactive get cookie by name. If **autoUpdateDependencies = true** then it will update watching dependencies
     */ (x2)
/**
       * Auto update watching dependencies if needed
       */
// eslint-disable-next-line ts/no-unused-expressions (x6)
/**
     * Reactive get all cookies
     */ (x2)
```

### `onChange(): void`

<details><summary>Code</summary>

```ts
() => {
    const newCookies = cookies.getAll({ doNotParse: true })

    if (
      shouldUpdate(
        watchingDependencies || null,
        newCookies,
        previousCookies,
      )
    ) {
      touches.value++
    }

    previousCookies = newCookies
  }
```
</details>

- **Return Type**: `void`
- **Calls**:
  - `cookies.getAll`
  - `shouldUpdate`
### `get(args: Parameters<Cookie['get']>): any`

<details><summary>Code</summary>

```ts
<T = any>(...args: Parameters<Cookie['get']>) => {
      /**
       * Auto update watching dependencies if needed
       */
      if (autoUpdateDependencies && watchingDependencies && !watchingDependencies.includes(args[0]))
        watchingDependencies.push(args[0])

      // eslint-disable-next-line ts/no-unused-expressions
      touches.value // adds reactivity to method
      return cookies.get<T>(args[0], { doNotParse, ...args[1] })
    }
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['get']>`
- **Return Type**: `any`
- **Calls**:
  - `watchingDependencies.includes`
  - `watchingDependencies.push`
  - `cookies.get`
- **Internal Comments**:
```
/**
       * Auto update watching dependencies if needed
       */
// eslint-disable-next-line ts/no-unused-expressions (x3)
```

### `getAll(args: Parameters<Cookie['getAll']>): any`

<details><summary>Code</summary>

```ts
<T = any>(...args: Parameters<Cookie['getAll']>) => {
      // eslint-disable-next-line ts/no-unused-expressions
      touches.value // adds reactivity to method
      return cookies.getAll<T>({ doNotParse, ...args[0] })
    }
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['getAll']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.getAll`
- **Internal Comments**:
```
// eslint-disable-next-line ts/no-unused-expressions (x3)
```

### `set(args: Parameters<Cookie['set']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['set']>) => cookies.set(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['set']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.set`
### `remove(args: Parameters<Cookie['remove']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['remove']>) => cookies.remove(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['remove']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.remove`
### `addChangeListener(args: Parameters<Cookie['addChangeListener']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['addChangeListener']>) => cookies.addChangeListener(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['addChangeListener']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.addChangeListener`
### `removeChangeListener(args: Parameters<Cookie['removeChangeListener']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['removeChangeListener']>) => cookies.removeChangeListener(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['removeChangeListener']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.removeChangeListener`
### `get(args: Parameters<Cookie['get']>): any`

<details><summary>Code</summary>

```ts
<T = any>(...args: Parameters<Cookie['get']>) => {
      /**
       * Auto update watching dependencies if needed
       */
      if (autoUpdateDependencies && watchingDependencies && !watchingDependencies.includes(args[0]))
        watchingDependencies.push(args[0])

      // eslint-disable-next-line ts/no-unused-expressions
      touches.value // adds reactivity to method
      return cookies.get<T>(args[0], { doNotParse, ...args[1] })
    }
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['get']>`
- **Return Type**: `any`
- **Calls**:
  - `watchingDependencies.includes`
  - `watchingDependencies.push`
  - `cookies.get`
- **Internal Comments**:
```
/**
       * Auto update watching dependencies if needed
       */
// eslint-disable-next-line ts/no-unused-expressions (x3)
```

### `getAll(args: Parameters<Cookie['getAll']>): any`

<details><summary>Code</summary>

```ts
<T = any>(...args: Parameters<Cookie['getAll']>) => {
      // eslint-disable-next-line ts/no-unused-expressions
      touches.value // adds reactivity to method
      return cookies.getAll<T>({ doNotParse, ...args[0] })
    }
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['getAll']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.getAll`
- **Internal Comments**:
```
// eslint-disable-next-line ts/no-unused-expressions (x3)
```

### `set(args: Parameters<Cookie['set']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['set']>) => cookies.set(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['set']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.set`
### `remove(args: Parameters<Cookie['remove']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['remove']>) => cookies.remove(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['remove']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.remove`
### `addChangeListener(args: Parameters<Cookie['addChangeListener']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['addChangeListener']>) => cookies.addChangeListener(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['addChangeListener']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.addChangeListener`
### `removeChangeListener(args: Parameters<Cookie['removeChangeListener']>): any`

<details><summary>Code</summary>

```ts
(...args: Parameters<Cookie['removeChangeListener']>) => cookies.removeChangeListener(...args)
```
</details>

- **Parameters**:
  - `args: Parameters<Cookie['removeChangeListener']>`
- **Return Type**: `any`
- **Calls**:
  - `cookies.removeChangeListener`
### `shouldUpdate(dependencies: string[] | null, newCookies: RawCookies, oldCookies: RawCookies): boolean`

<details><summary>Code</summary>

```ts
function shouldUpdate(
  dependencies: string[] | null,
  newCookies: RawCookies,
  oldCookies: RawCookies,
) {
  if (!dependencies)
    return true

  for (const dependency of dependencies) {
    if (newCookies[dependency] !== oldCookies[dependency])
      return true
  }

  return false
}
```
</details>

- **Parameters**:
  - `dependencies: string[] | null`
  - `newCookies: RawCookies`
  - `oldCookies: RawCookies`
- **Return Type**: `boolean`

---

## Type Aliases

### `RawCookies`

```ts
type RawCookies = Record<string, string>;
```


---