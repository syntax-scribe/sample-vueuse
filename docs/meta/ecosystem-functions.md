[⬅️ Back to Table of Contents](../index.md)

# 📄 `ecosystem-functions.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 1 |
| 📊 Variables & Constants | 6 |
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

## 🛠️ File Location:
📂 **`meta/ecosystem-functions.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `VueUseFunction` | `@vueuse/metadata` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `head` | `VueUseFunction[]` | const | `[
  {
    name: 'createHead',
    package: 'head',
    description: 'create the head manager instance.',
    category: '@Head',
    external: 'https://github.com/vueuse/head#api',
  },
  {
    name: 'useHead',
    package: 'head',
    description: 'update head meta tags reactively.',
    category: '@Head',
    external: 'https://github.com/vueuse/head#api',
  },
]` | ✓ |
| `motionDefaults` | `{ package: string; category: string; }` | const | `{
  package: 'motion',
  category: '@Motion',
}` | ✗ |
| `motion` | `VueUseFunction[]` | const | `[
  {
    ...motionDefaults,
    name: 'useMotion',
    description: 'putting your components in motion.',
    external: 'https://motion.vueuse.org/api/use-motion',
  },
  {
    ...motionDefaults,
    name: 'useSpring',
    description: 'spring animations.',
    external: 'https://motion.vueuse.org/api/use-spring',
  },
  {
    ...motionDefaults,
    name: 'useMotionProperties',
    description: 'access Motion Properties for a target element.',
    external: 'https://motion.vueuse.org/api/use-motion-properties',
  },
  {
    ...motionDefaults,
    name: 'useMotionVariants',
    description: 'handle the Variants state and selection.',
    external: 'https://motion.vueuse.org/api/use-motion-variants',
  },
  {
    ...motionDefaults,
    name: 'useElementStyle',
    description: 'sync a reactive object to a target element CSS styling',
    external: 'https://motion.vueuse.org/api/use-element-style',
  },
  {
    ...motionDefaults,
    name: 'useElementTransform',
    description: 'sync a reactive object to a target element CSS transform.',
    external: 'https://motion.vueuse.org/api/use-element-transform',
  },
]` | ✓ |
| `sound` | `VueUseFunction[]` | const | `[
  {
    name: 'useSound',
    package: 'sound',
    description: 'play sound effects reactively.',
    category: '@Sound',
    external: 'https://github.com/vueuse/sound#examples',
  },
]` | ✓ |
| `schemaOrg` | `VueUseFunction[]` | const | `[
  {
    name: 'createSchemaOrg',
    package: 'schema-org',
    description: 'create the schema.org manager instance.',
    category: '@SchemaOrg',
    external: 'https://vue-schema-org.netlify.app/api/core/create-schema-org.html',
  },
  {
    name: 'useSchemaOrg',
    package: 'schema-org',
    description: 'update schema.org reactively.',
    category: '@SchemaOrg',
    external: 'https://vue-schema-org.netlify.app/api/core/use-schema-org.html',
  },
]` | ✓ |
| `ecosystemFunctions` | `any[]` | const | `[
  ...head,
  ...motion,
  ...schemaOrg,
  ...sound,
]` | ✓ |


---

## 🔧 Functions

> No functions found in this file.


---