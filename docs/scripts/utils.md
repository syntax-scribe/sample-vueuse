[⬅️ Back to Table of Contents](../index.md)

# 📄 `utils.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 13 |
| 🧱 Classes | 0 |
| 📦 Imports | 12 |
| 📊 Variables & Constants | 24 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 10 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Async/Await Patterns](#asyncawait-patterns)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`scripts/utils.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `PackageIndexes` | `@vueuse/metadata` |
| `VueUseFunction` | `@vueuse/metadata` |
| `existsSync` | `node:fs` |
| `join` | `node:path` |
| `resolve` | `node:path` |
| `fileURLToPath` | `node:url` |
| `matter` | `gray-matter` |
| `$fetch` | `ofetch` |
| `Git` | `simple-git` |
| `yaml` | `yaml` |
| `packages` | `../meta/packages` |
| `getCategories` | `../packages/metadata/utils` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `DOCS_URL` | `"https://vueuse.org"` | const | `'https://vueuse.org'` | ✓ |
| `types` | `string` | let/var | `await fs.readFile(typingFilepath, 'utf-8')` | ✗ |
| `prettier` | `any` | let/var | `await import('prettier')` | ✗ |
| `imports` | `string[]` | let/var | `*not shown*` | ✗ |
| `arr` | `string[]` | const | `[]` | ✗ |
| `list` | `string` | let/var | `''` | ✗ |
| `desc` | `string` | const | `description ? ` — ${description}` : ''` | ✗ |
| `START` | `string` | const | ``<!--${key}_STARTS-->`` | ✗ |
| `END` | `string` | const | ``<!--${key}_ENDS-->`` | ✗ |
| `regex` | `RegExp` | const | `new RegExp(`${START}[\\s\\S]*?${END}`, 'im')` | ✗ |
| `target` | `string` | const | `value ? `${START}\n\n${value.trim()}\n\n${END}` : `${START}${END}`` | ✗ |
| `readme` | `string` | let/var | `await fs.readFile(readmePath, 'utf-8')` | ✗ |
| `readme` | `string` | let/var | `await fs.readFile('README.md', 'utf-8')` | ✗ |
| `functionsCount` | `any` | let/var | `functions.filter(i => !i.internal).length` | ✗ |
| `mdAddons` | `string` | let/var | `await fs.readFile('packages/add-ons.md', 'utf-8')` | ✗ |
| `mdPath` | `string` | let/var | ``packages/${fn.package}/${fn.name}/index.md`` | ✗ |
| `readme` | `string` | let/var | `await fs.readFile(mdPath, 'utf-8')` | ✗ |
| `functionsCount` | `any` | let/var | `indexes.functions.filter(i => !i.internal).length` | ✗ |
| `url` | `string` | let/var | ``https://img.shields.io/badge/-${functionsCount}%20functions-13708a`` | ✗ |
| `data` | `any` | let/var | `await $fetch(url, { responseType: 'text' })` | ✗ |
| `additional` | `string[]` | let/var | `['egoist', 'Tahul', 'BobbieGoede']` | ✗ |
| `collaborators` | `string[]` | let/var | `[]` | ✗ |
| `data` | `any` | let/var | `await $fetch<{ login: string }[]>(`https://api.github.com/repos/vueuse/vueuse/contributors?per_page=100&page=${page}`, {
    method: 'get',
    headers: {
      'content-type': 'application/json',
    },
  }) || []` | ✗ |
| `collaborators` | `string[]` | let/var | `await fetchContributors()` | ✗ |


---

## Async/Await Patterns

| Type | Function | Await Expressions | Promise Chains |
|------|----------|-------------------|----------------|
| async-function | `getTypeDefinition` | fs.readFile(typingFilepath, 'utf-8'), import('prettier'), prettier
    .format(
      types,
      {
        semi: false,
        parser: 'typescript',
      },
    ) | *none* |
| async-function | `updateImport` | fs.writeFile(join(dir, 'index.ts'), `${imports.join('\n')}\n`), fs.rm(join(dir, 'index.mjs'), { force: true }) | *none* |
| async-function | `updatePackageREADME` | fs.readFile(readmePath, 'utf-8'), fs.writeFile(readmePath, `${readme}\n`, 'utf-8') | *none* |
| async-function | `updateIndexREADME` | fs.readFile('README.md', 'utf-8'), fs.writeFile('README.md', `${readme}\n`, 'utf-8') | *none* |
| async-function | `updateFunctionsMD` | fs.readFile('packages/add-ons.md', 'utf-8'), fs.writeFile('packages/add-ons.md', mdAddons, 'utf-8') | *none* |
| async-function | `updateFunctionREADME` | fs.readFile(mdPath, 'utf-8'), fs.writeFile(mdPath, `${readme}\n`, 'utf-8') | *none* |
| async-function | `updateCountBadge` | $fetch(url, { responseType: 'text' }), fs.writeFile(join(DIR_ROOT, 'packages/public/badge-function-count.svg'), data, 'utf-8') | *none* |
| async-function | `updatePackageJSON` | fs.readFile('package.json', { encoding: 'utf8' }), fs.readFile(packageJSONPath, { encoding: 'utf8' }), fs.writeFile(packageJSONPath, `${JSON.stringify(packageJSON, null, 2)}\n`) | *none* |
| async-function | `fetchContributors` | $fetch<{ login: string }[]>(`https://api.github.com/repos/vueuse/vueuse/contributors?per_page=100&page=${page}`, {
    method: 'get',
    headers: {
      'content-type': 'application/json',
    },
  }), fetchContributors(page + 1) | *none* |
| async-function | `updateContributors` | fetchContributors(), fs.writeFile(join(DIR_SRC, './contributors.json'), `${JSON.stringify(collaborators, null, 2)}\n`, 'utf8') | *none* |


---

## Functions

### `getTypeDefinition(pkg: string, name: string): Promise<string | undefined>`

<details><summary>Code</summary>

```ts
export async function getTypeDefinition(pkg: string, name: string): Promise<string | undefined> {
  const typingFilepath = join(DIR_TYPES, `${pkg}/${name}/index.d.ts`)

  if (!existsSync(typingFilepath))
    return

  let types = await fs.readFile(typingFilepath, 'utf-8')

  if (!types)
    return

  // clean up types
  types = types
    .replace(/import\(.*?\)\./g, '')
    .replace(/import[\s\S]+?from ?["'][\s\S]+?["']/g, '')
    .replace(/export \{\}/g, '')

  const prettier = await import('prettier')
  return (await prettier
    .format(
      types,
      {
        semi: false,
        parser: 'typescript',
      },
    ))
    .trim()
}
```
</details>

- **Parameters**:
  - `pkg: string`
  - `name: string`
- **Return Type**: `Promise<string | undefined>`
- **Calls**:
  - `join (from node:path)`
  - `existsSync (from node:fs)`
  - `fs.readFile`
  - `types
    .replace(/import\(.*?\)\./g, '')
    .replace(/import[\s\S]+?from ?["'][\s\S]+?["']/g, '')
    .replace`
  - `complex_call_1243`
  - `(await prettier
    .format(
      types,
      {
        semi: false,
        parser: 'typescript',
      },
    ))
    .trim`
  - `prettier
    .format`
- **Internal Comments**:
```
// clean up types (x3)
```

### `updateImport({ packages, functions }: PackageIndexes): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updateImport({ packages, functions }: PackageIndexes) {
  for (const { name, dir, manualImport } of Object.values(packages)) {
    if (manualImport)
      continue

    let imports: string[]
    if (name === 'components') {
      imports = functions
        .sort((a, b) => a.name.localeCompare(b.name))
        .flatMap((fn) => {
          const arr: string[] = []

          // don't include integration components
          if (fn.package === 'integrations')
            return arr

          if (fn.component)
            arr.push(`export * from '../${fn.package}/${fn.name}/component'`)
          if (fn.directive)
            arr.push(`export * from '../${fn.package}/${fn.name}/directive'`)
          return arr
        })
    }
    else {
      imports = functions
        .filter(i => i.package === name)
        .map(f => f.name)
        .sort()
        .map(name => `export * from './${name}'`)
    }

    if (name === 'core') {
      imports.push(
        'export * from \'./types\'',
        'export * from \'@vueuse/shared\'',
        'export * from \'./ssr-handlers\'',
      )
    }

    if (name === 'nuxt') {
      imports.push(
        'export * from \'@vueuse/core\'',
      )
    }

    await fs.writeFile(join(dir, 'index.ts'), `${imports.join('\n')}\n`)

    // temporary file for export-size
    await fs.rm(join(dir, 'index.mjs'), { force: true })
  }
}
```
</details>

- **Parameters**:
  - `{ packages, functions }: PackageIndexes`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `Object.values`
  - `functions
        .sort((a, b) => a.name.localeCompare(b.name))
        .flatMap`
  - `arr.push`
  - `functions
        .filter(i => i.package === name)
        .map(f => f.name)
        .sort()
        .map`
  - `imports.push`
  - `fs.writeFile`
  - `join (from node:path)`
  - `imports.join`
  - `fs.rm`
- **Internal Comments**:
```
// don't include integration components
// temporary file for export-size (x2)
```

### `uniq(a: T): any[]`

<details><summary>Code</summary>

```ts
export function uniq<T extends any[]>(a: T) {
  return Array.from(new Set(a))
}
```
</details>

- **Parameters**:
  - `a: T`
- **Return Type**: `any[]`
- **Calls**:
  - `Array.from`
### `stringifyFunctions(functions: VueUseFunction[], title: boolean): string`

<details><summary>Code</summary>

```ts
export function stringifyFunctions(functions: VueUseFunction[], title = true) {
  let list = ''

  const categories = getCategories(functions)

  for (const category of categories) {
    if (category.startsWith('_'))
      continue

    if (title)
      list += `### ${category}\n`

    const categoryFunctions = functions
      .filter(i => i.category === category)
      .sort((a, b) => a.name.localeCompare(b.name))

    for (const { name, docs, description, deprecated } of categoryFunctions) {
      if (deprecated)
        continue

      const desc = description ? ` — ${description}` : ''
      list += `- [\`${name}\`](${docs})${desc}\n`
    }
    list += '\n'
  }
  return list
}
```
</details>

- **Parameters**:
  - `functions: VueUseFunction[]`
  - `title: boolean`
- **Return Type**: `string`
- **Calls**:
  - `getCategories (from ../packages/metadata/utils)`
  - `category.startsWith`
  - `functions
      .filter(i => i.category === category)
      .sort`
  - `a.name.localeCompare`
### `replacer(code: string, value: string, key: string, insert: 'head' | 'tail' | 'none'): string`

<details><summary>Code</summary>

```ts
export function replacer(code: string, value: string, key: string, insert: 'head' | 'tail' | 'none' = 'none') {
  const START = `<!--${key}_STARTS-->`
  const END = `<!--${key}_ENDS-->`
  const regex = new RegExp(`${START}[\\s\\S]*?${END}`, 'im')

  const target = value ? `${START}\n\n${value.trim()}\n\n${END}` : `${START}${END}`

  if (!code.match(regex)) {
    if (insert === 'none')
      return code
    else if (insert === 'head')
      return `${target}\n\n${code}`
    else
      return `${code}\n\n${target}`
  }

  return code.replace(regex, target)
}
```
</details>

- **Parameters**:
  - `code: string`
  - `value: string`
  - `key: string`
  - `insert: 'head' | 'tail' | 'none'`
- **Return Type**: `string`
- **Calls**:
  - `value.trim`
  - `code.match`
  - `code.replace`
### `updatePackageREADME({ packages, functions }: PackageIndexes): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updatePackageREADME({ packages, functions }: PackageIndexes) {
  for (const { name, dir } of Object.values(packages)) {
    const readmePath = join(dir, 'README.md')

    if (!existsSync(readmePath))
      continue

    const functionMD = stringifyFunctions(functions.filter(i => i.package === name), false)
    let readme = await fs.readFile(readmePath, 'utf-8')
    readme = replacer(readme, functionMD, 'FUNCTIONS_LIST').trim().replace(/\r\n/g, '\n')

    await fs.writeFile(readmePath, `${readme}\n`, 'utf-8')
  }
}
```
</details>

- **Parameters**:
  - `{ packages, functions }: PackageIndexes`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `Object.values`
  - `join (from node:path)`
  - `existsSync (from node:fs)`
  - `stringifyFunctions`
  - `functions.filter`
  - `fs.readFile`
  - `replacer(readme, functionMD, 'FUNCTIONS_LIST').trim().replace`
  - `fs.writeFile`
### `updateIndexREADME({ packages, functions }: PackageIndexes): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updateIndexREADME({ packages, functions }: PackageIndexes) {
  let readme = await fs.readFile('README.md', 'utf-8')

  const functionsCount = functions.filter(i => !i.internal).length

  readme = readme.replace(
    /img\.shields\.io\/badge\/-(.+?)%20functions/,
    `img.shields.io/badge/-${functionsCount}%20functions`,
  ).trim().replace(/\r\n/g, '\n')

  await fs.writeFile('README.md', `${readme}\n`, 'utf-8')
}
```
</details>

- **Parameters**:
  - `{ packages, functions }: PackageIndexes`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `fs.readFile`
  - `functions.filter`
  - `readme.replace(
    /img\.shields\.io\/badge\/-(.+?)%20functions/,
    `img.shields.io/badge/-${functionsCount}%20functions`,
  ).trim().replace`
  - `fs.writeFile`
### `updateFunctionsMD({ packages, functions }: PackageIndexes): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updateFunctionsMD({ packages, functions }: PackageIndexes) {
  let mdAddons = await fs.readFile('packages/add-ons.md', 'utf-8')

  const addons = Object.values(packages)
    .filter(i => i.addon && !i.deprecated)
    .map(({ docs, name, display, description }) => {
      return `## ${display} - [\`@vueuse/${name}\`](${docs})\n\n${description?.trim()}\n\n${
        stringifyFunctions(functions.filter(i => i.package === name), false)}`.trim()
    })
    .join('\n\n')

  mdAddons = replacer(mdAddons, addons, 'ADDONS_LIST').replace(/\r\n/g, '\n')

  await fs.writeFile('packages/add-ons.md', mdAddons, 'utf-8')
}
```
</details>

- **Parameters**:
  - `{ packages, functions }: PackageIndexes`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `fs.readFile`
  - `Object.values(packages)
    .filter(i => i.addon && !i.deprecated)
    .map(({ docs, name, display, description }) => {
      return `## ${display} - [\`@vueuse/${name}\`](${docs})\n\n${description?.trim()}\n\n${
        stringifyFunctions(functions.filter(i => i.package === name), false)}`.trim()
    })
    .join`
  - `replacer(mdAddons, addons, 'ADDONS_LIST').replace`
  - `fs.writeFile`
### `updateFunctionREADME(indexes: PackageIndexes): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updateFunctionREADME(indexes: PackageIndexes) {
  const hasTypes = existsSync(DIR_TYPES)

  if (!hasTypes)
    console.warn('No types dist found, run `npm run build:types` first.')

  for (const fn of indexes.functions) {
    const mdPath = `packages/${fn.package}/${fn.name}/index.md`
    if (!existsSync(mdPath))
      continue

    let readme = await fs.readFile(mdPath, 'utf-8')

    const { content, data = {} } = matter(readme)
    const yamlData = yaml.stringify(data, {
      singleQuote: true,
    })

    data.category = fn.category || 'Unknown'

    readme = `---\n${yamlData}---\n\n${content.trim()}`.trim().replace(/\r\n/g, '\n')

    await fs.writeFile(mdPath, `${readme}\n`, 'utf-8')
  }
}
```
</details>

- **Parameters**:
  - `indexes: PackageIndexes`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `existsSync (from node:fs)`
  - `console.warn`
  - `fs.readFile`
  - `matter (from gray-matter)`
  - `yaml.stringify`
  - ``---\n${yamlData}---\n\n${content.trim()}`.trim().replace`
  - `fs.writeFile`
### `updateCountBadge(indexes: PackageIndexes): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updateCountBadge(indexes: PackageIndexes) {
  const functionsCount = indexes.functions.filter(i => !i.internal).length
  const url = `https://img.shields.io/badge/-${functionsCount}%20functions-13708a`
  const data = await $fetch(url, { responseType: 'text' })
  await fs.writeFile(join(DIR_ROOT, 'packages/public/badge-function-count.svg'), data, 'utf-8')
}
```
</details>

- **Parameters**:
  - `indexes: PackageIndexes`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `indexes.functions.filter`
  - `$fetch (from ofetch)`
  - `fs.writeFile`
  - `join (from node:path)`
### `updatePackageJSON(indexes: PackageIndexes): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updatePackageJSON(indexes: PackageIndexes) {
  const { version } = JSON.parse(await fs.readFile('package.json', { encoding: 'utf8' }))

  for (const { name, description, author, submodules, iife } of packages) {
    const packageDir = join(DIR_SRC, name)
    const packageJSONPath = join(packageDir, 'package.json')
    const packageJSON = JSON.parse(await fs.readFile(packageJSONPath, { encoding: 'utf8' }))

    packageJSON.version = version
    packageJSON.description = description || packageJSON.description
    packageJSON.author = author || 'Anthony Fu <https://github.com/antfu>'
    packageJSON.bugs = {
      url: 'https://github.com/vueuse/vueuse/issues',
    }
    packageJSON.type = 'module'
    packageJSON.homepage = name === 'core'
      ? 'https://github.com/vueuse/vueuse#readme'
      : `https://github.com/vueuse/vueuse/tree/main/packages/${name}#readme`
    packageJSON.repository = {
      type: 'git',
      url: 'git+https://github.com/vueuse/vueuse.git',
      directory: `packages/${name}`,
    }
    packageJSON.main = './index.mjs'
    packageJSON.types = './index.d.mts'
    packageJSON.module = './index.mjs'
    if (iife !== false) {
      packageJSON.unpkg = './index.iife.min.js'
      packageJSON.jsdelivr = './index.iife.min.js'
    }
    packageJSON.files = [
      '*.d.mts',
      '*.js',
      '*.mjs',
    ]

    if (submodules) {
      packageJSON.files = packageJSON.files.map((i: string) => `**/${i}`)
    }

    if (name === 'metadata') {
      packageJSON.files.push('index.json')
    }

    packageJSON.exports = {
      '.': './index.mjs',
      ...packageJSON.exports,
      './*': './*',
    }

    if (submodules) {
      indexes.functions
        .filter(i => i.package === name)
        .forEach((i) => {
          packageJSON.exports[`./${i.name}`] = `./${i.name}.mjs`
          if (i.component) {
            packageJSON.exports[`./${i.name}/component`] = `./${i.name}/component.mjs`
          }
        })
    }

    await fs.writeFile(packageJSONPath, `${JSON.stringify(packageJSON, null, 2)}\n`)
  }
}
```
</details>

- **Parameters**:
  - `indexes: PackageIndexes`
- **Return Type**: `Promise<void>`
- **Calls**:
  - `JSON.parse`
  - `fs.readFile`
  - `join (from node:path)`
  - `packageJSON.files.map`
  - `packageJSON.files.push`
  - `indexes.functions
        .filter(i => i.package === name)
        .forEach`
  - `fs.writeFile`
  - `JSON.stringify`
### `fetchContributors(page: number): Promise<string[]>`

<details><summary>Code</summary>

```ts
async function fetchContributors(page = 1) {
  // contributors that contribute to repos other than `vueuse/vueuse`, required for contributor avatar to work
  const additional = ['egoist', 'Tahul', 'BobbieGoede']

  const collaborators: string[] = []
  const data = await $fetch<{ login: string }[]>(`https://api.github.com/repos/vueuse/vueuse/contributors?per_page=100&page=${page}`, {
    method: 'get',
    headers: {
      'content-type': 'application/json',
    },
  }) || []
  collaborators.push(...data.map(i => i.login))
  if (data.length === 100)
    collaborators.push(...(await fetchContributors(page + 1)))

  return Array.from(new Set([
    ...collaborators.filter(collaborator => !['renovate[bot]', 'dependabot[bot]', 'renovate-bot'].includes(collaborator)),
    ...additional,
  ]))
}
```
</details>

- **Parameters**:
  - `page: number`
- **Return Type**: `Promise<string[]>`
- **Calls**:
  - `$fetch (from ofetch)`
  - `collaborators.push`
  - `data.map`
  - `fetchContributors`
  - `Array.from`
  - `collaborators.filter`
  - `['renovate[bot]', 'dependabot[bot]', 'renovate-bot'].includes`
- **Internal Comments**:
```
// contributors that contribute to repos other than `vueuse/vueuse`, required for contributor avatar to work (x2)
```

### `updateContributors(): Promise<void>`

<details><summary>Code</summary>

```ts
export async function updateContributors() {
  const collaborators = await fetchContributors()
  await fs.writeFile(join(DIR_SRC, './contributors.json'), `${JSON.stringify(collaborators, null, 2)}\n`, 'utf8')
}
```
</details>

- **Return Type**: `Promise<void>`
- **Calls**:
  - `fetchContributors`
  - `fs.writeFile`
  - `join (from node:path)`
  - `JSON.stringify`

---