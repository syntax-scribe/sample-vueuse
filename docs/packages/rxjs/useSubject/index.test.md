[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.test.ts`

## 📊 Analysis Summary

| Metric | Count |
|--------|-------|
| 🔧 Functions | 0 |
| 🧱 Classes | 0 |
| 📦 Imports | 9 |
| 📊 Variables & Constants | 4 |
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
📂 **`packages/rxjs/useSubject/index.test.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `BehaviorSubject` | `rxjs` |
| `Subject` | `rxjs` |
| `first` | `rxjs/operators` |
| `skip` | `rxjs/operators` |
| `describe` | `vitest` |
| `expect` | `vitest` |
| `it` | `vitest` |
| `useInjectedSetup` | `../../.test` |
| `useSubject` | `./index` |


---

## Variables & Constants

| Name | Type | Kind | Value | Exported |
|------|------|------|-------|----------|
| `subject` | `any` | const | `new Subject<boolean>()` | ✗ |
| `subject` | `any` | const | `new BehaviorSubject(false)` | ✗ |
| `subject` | `any` | let/var | `new BehaviorSubject(false)` | ✗ |
| `value` | `unknown` | let/var | `await new Promise((resolve) => {
      subject.pipe(skip(1), first()).subscribe(resolve)

      const subjectRef = useSubject(subject)

      subjectRef.value = true
    })` | ✗ |


---

## 🔧 Functions

> No functions found in this file.


---