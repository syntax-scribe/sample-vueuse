[⬅️ Back to Table of Contents](../../../../index.md)

# 📄 `depsParser.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📊 Variables & Constants | 2 |

## 📚 Table of Contents

- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`packages/core/useWebWorkerFn/lib/depsParser.ts`**

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `name` | `string` | const | `fn.name` | ✗ |
| `importString` | `string` | const | ``importScripts(${depsString});`` | ✗ |


---

## Functions

### `depsParser(deps: string[], localDeps: Function[]): string`

<details><summary>Code</summary>

```ts
function depsParser(deps: string[], localDeps: Function[]) {
  if (deps.length === 0 && localDeps.length === 0)
    return ''

  const depsString = deps.map(dep => `'${dep}'`).toString()
  const depsFunctionString = localDeps.filter(dep => typeof dep === 'function').map((fn) => {
    const str = fn.toString()
    if (str.trim().startsWith('function')) {
      return str
    }
    else {
      const name = fn.name
      return `const ${name} = ${str}`
    }
  }).join(';')
  const importString = `importScripts(${depsString});`

  return `${depsString.trim() === '' ? '' : importString} ${depsFunctionString}`
}
```
</details>

- **JSDoc**:
```ts
/**
 *
 * Concatenates the dependencies into a comma separated string.
 * this string will then be passed as an argument to the "importScripts" function
 *
 * @param deps array of string
 * @param localDeps array of function
 * @returns a string composed by the concatenation of the array
 * elements "deps" and "importScripts".
 *
 * @example
 * depsParser(['demo1', 'demo2']) // return importScripts('demo1', 'demo2')
 */
```

- **Parameters**:
  - `deps: string[]`
  - `localDeps: Function[]`
- **Return Type**: `string`
- **Calls**:
  - `deps.map(dep => `'${dep}'`).toString`
  - `localDeps.filter(dep => typeof dep === 'function').map((fn) => {
    const str = fn.toString()
    if (str.trim().startsWith('function')) {
      return str
    }
    else {
      const name = fn.name
      return `const ${name} = ${str}`
    }
  }).join`
  - `depsString.trim`

---