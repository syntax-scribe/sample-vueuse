[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 1 |
| 📦 Imports | 7 |
| 📊 Variables & Constants | 4 |
| 📐 Interfaces | 1 |
| 📑 Type Aliases | 1 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 🛠️ File Location:
📂 **`packages/integrations/useChangeCase/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `Options` | `change-case` |
| `ChangeCaseType` | `./index` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `deepRef` | `vue` |
| `useChangeCase` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `helloWorld` | `"helloWorld"` | const | `'helloWorld'` | ✗ |
| `vueuse` | `"vue use"` | const | `'vue use'` | ✗ |
| `obj` | `ObjectTypes` | const | `{
    capitalCase: {
      helloWorld: 'Hello World',
      vueuse: 'Vue Use',
      delimiterHelloWorld: 'Hello-World',
      delimiterVueuse: 'Vue-Use',
    },
    constantCase: {
      helloWorld: 'HELLO_WORLD',
      vueuse: 'VUE_USE',
      delimiterHelloWorld: 'HELLO-WORLD',
      delimiterVueuse: 'VUE-USE',
    },
    dotCase: {
      helloWorld: 'hello.world',
      vueuse: 'vue.use',
      delimiterHelloWorld: 'hello-world',
      delimiterVueuse: 'vue-use',
    },
    trainCase: {
      helloWorld: 'Hello-World',
      vueuse: 'Vue-Use',
      delimiterHelloWorld: 'Hello-World',
      delimiterVueuse: 'Vue-Use',
    },
    noCase: {
      helloWorld: 'hello world',
      vueuse: 'vue use',
      delimiterHelloWorld: 'hello-world',
      delimiterVueuse: 'vue-use',
    },
    kebabCase: {
      helloWorld: 'hello-world',
      vueuse: 'vue-use',
      delimiterHelloWorld: 'hello-world',
      delimiterVueuse: 'vue-use',
    },
    pascalCase: {
      helloWorld: 'HelloWorld',
      vueuse: 'VueUse',
      delimiterHelloWorld: 'Hello-World',
      delimiterVueuse: 'Vue-Use',
    },
    pascalSnakeCase: {
      helloWorld: 'Hello_World',
      vueuse: 'Vue_Use',
      delimiterHelloWorld: 'Hello-World',
      delimiterVueuse: 'Vue-Use',
    },
    pathCase: {
      helloWorld: 'hello/world',
      vueuse: 'vue/use',
      delimiterHelloWorld: 'hello-world',
      delimiterVueuse: 'vue-use',
    },
    sentenceCase: {
      helloWorld: 'Hello world',
      vueuse: 'Vue use',
      delimiterHelloWorld: 'Hello-world',
      delimiterVueuse: 'Vue-use',
    },
    snakeCase: {
      helloWorld: 'hello_world',
      vueuse: 'vue_use',
      delimiterHelloWorld: 'hello-world',
      delimiterVueuse: 'vue-use',
    },
  }` | ✗ |
| `options` | `Options` | const | `{
        delimiter: '-',
      }` | ✗ |


---

## Functions

### `input(): string`

<details><summary>Code</summary>

```ts
() => helloWorld
```
</details>

- **Return Type**: `string`

---

## Interfaces

### `objectValue`

<details><summary>Interface Code</summary>

```ts
interface objectValue {
    helloWorld: string
    vueuse: string
    delimiterHelloWorld: string
    delimiterVueuse: string
  }
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `helloWorld` | `string` | ✗ |  |
| `vueuse` | `string` | ✗ |  |
| `delimiterHelloWorld` | `string` | ✗ |  |
| `delimiterVueuse` | `string` | ✗ |  |


---

## Type Aliases

### `ObjectTypes`

```ts
type ObjectTypes = Omit<Record<ChangeCaseType, objectValue>, 'camelCase'>;
```


---