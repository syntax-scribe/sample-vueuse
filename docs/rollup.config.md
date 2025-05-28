[⬅️ Back to Table of Contents](index.md)

# 📄 `rollup.config.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 2 |
| 🧱 Classes | 0 |
| 📦 Imports | 11 |
| 📊 Variables & Constants | 8 |
| ✨ Decorators | 0 |
| 🔄 Re-exports | 0 |
| ⚡ Async/Await Patterns | 0 |
| 💠 JSX Elements | 0 |
| 🟢 Vue Composition API | 0 |
| 📐 Interfaces | 0 |
| 📑 Type Aliases | 0 |
| 🎯 Enums | 0 |

## 📚 Table of Contents

- [Imports](#imports)
- [Variables & Constants](#variables-constants)
- [Functions](#functions)

## 🛠️ File Location:
📂 **`rollup.config.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `PackageIndexes` | `@vueuse/metadata` |
| `PackageManifest` | `@vueuse/metadata` |
| `OutputOptions` | `rollup` |
| `RollupOptions` | `rollup` |
| `ESBuildOptions` | `rollup-plugin-esbuild` |
| `fs` | `node:fs` |
| `json` | `@rollup/plugin-json` |
| `dts` | `rollup-plugin-dts` |
| `esbuild` | `rollup-plugin-esbuild` |
| `pure` | `rollup-plugin-pure` |
| `globSync` | `tinyglobby` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `functions` | `PackageIndexes` | const | `metadata.functions as PackageIndexes['functions']` | ✗ |
| `configs` | `RollupOptions[]` | const | `[]` | ✗ |
| `externals` | `(string | RegExp)[]` | const | `[
  'vue',
  /@vueuse\/.*/,
]` | ✗ |
| `iifeGlobals` | `any` | const | `{
    'vue': 'Vue',
    '@vueuse/shared': 'VueUse',
    '@vueuse/core': 'VueUse',
    ...(globals || {}),
  }` | ✗ |
| `iifeName` | `"VueUse"` | const | `'VueUse'` | ✗ |
| `functionNames` | `string[]` | const | `['index']` | ✗ |
| `input` | `string` | const | `fn === 'index'
      ? `index.ts`
      : `${fn}/index.ts`` | ✗ |
| `output` | `OutputOptions[]` | const | `[]` | ✗ |


---

## Functions

### `esbuildMinifier(options: ESBuildOptions): { name: string; renderChunk: any; }`

<details><summary>Code</summary>

```ts
function esbuildMinifier(options: ESBuildOptions) {
  const { renderChunk } = esbuild(options)

  return {
    name: 'esbuild-minifier',
    renderChunk,
  }
}
```
</details>

- **Parameters**:
  - `options: ESBuildOptions`
- **Return Type**: `{ name: string; renderChunk: any; }`
- **Calls**:
  - `esbuild (from rollup-plugin-esbuild)`
### `createRollupConfig(pkg: PackageManifest, cwd: string): RollupOptions[]`

<details><summary>Code</summary>

```ts
export function createRollupConfig(
  pkg: PackageManifest,
  cwd = process.cwd(),
) {
  const { globals, external, submodules, iife, build, mjs, dts, target = 'es2018' } = pkg
  if (build === false)
    return []

  const iifeGlobals = {
    'vue': 'Vue',
    '@vueuse/shared': 'VueUse',
    '@vueuse/core': 'VueUse',
    ...(globals || {}),
  }

  const iifeName = 'VueUse'
  const functionNames = ['index']

  if (submodules) {
    functionNames.push(...globSync(
      '*/index.ts',
      { cwd },
    ).map(i => i.split('/')[0]))
  }

  for (const fn of functionNames) {
    const input = fn === 'index'
      ? `index.ts`
      : `${fn}/index.ts`

    const info = functions.find(i => i.name === fn)

    const output: OutputOptions[] = []

    if (mjs !== false) {
      output.push({
        file: `${fn}.mjs`,
        format: 'es',
      })
    }

    if (iife !== false) {
      output.push(
        {
          file: `${fn}.iife.js`,
          format: 'iife',
          name: iifeName,
          extend: true,
          globals: iifeGlobals,
          plugins: [],
        },
        {
          file: `${fn}.iife.min.js`,
          format: 'iife',
          name: iifeName,
          extend: true,
          globals: iifeGlobals,
          plugins: [
            esbuildMinifier({
              minify: true,
            }),
          ],
        },
      )
    }

    configs.push({
      input,
      output,
      plugins: [
        target
          ? esbuild({ target })
          : pluginEsbuild,
        json(),
        pluginPure,
      ],
      external: [
        ...externals,
        ...(external || []),
      ],
    })

    if (dts !== false) {
      configs.push({
        input,
        output: [
          { file: `${fn}.d.mts` },
        ],
        plugins: [
          pluginDts,
        ],
        external: [
          ...externals,
          ...(external || []),
        ],
      })
    }

    if (info?.component) {
      configs.push({
        input: `${fn}/component.ts`,
        output: [
          {
            file: `${fn}/component.mjs`,
            format: 'es',
          },
        ],
        plugins: [
          pluginEsbuild,
          pluginPure,
        ],
        external: [
          ...externals,
          ...(external || []),
        ],
      })

      configs.push({
        input: `${fn}/component.ts`,
        output: [
          { file: `${fn}/component.d.mts` },
        ],
        plugins: [
          pluginDts,
        ],
        external: [
          ...externals,
          ...(external || []),
        ],
      })
    }
  }

  return configs
}
```
</details>

- **Parameters**:
  - `pkg: PackageManifest`
  - `cwd: string`
- **Return Type**: `RollupOptions[]`
- **Calls**:
  - `functionNames.push`
  - `globSync(
      '*/index.ts',
      { cwd },
    ).map`
  - `i.split`
  - `functions.find`
  - `output.push`
  - `esbuildMinifier`
  - `configs.push`
  - `esbuild (from rollup-plugin-esbuild)`
  - `json (from @rollup/plugin-json)`

---