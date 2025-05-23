[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `types.ts`

## 📚 Table of Contents

- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 0
- **Classes**: 0
- **Imports**: 0
- **Interfaces**: 8
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useSpeechRecognition/types.ts`**

## 📦 Imports

> No imports found in this file.


---

## 🔧 Functions

> No functions found in this file.


---

## Classes

> No classes found in this file.


---

## Interfaces

### `SpeechRecognitionErrorEventInit`

<details><summary>Interface Code</summary>

```ts
export interface SpeechRecognitionErrorEventInit extends EventInit {
  error: SpeechRecognitionErrorCode
  message?: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `error` | `SpeechRecognitionErrorCode` | ✗ |  |
| `message` | `string` | ✓ |  |

### `SpeechRecognitionEventInit`

<details><summary>Interface Code</summary>

```ts
export interface SpeechRecognitionEventInit extends EventInit {
  resultIndex?: number
  results: SpeechRecognitionResultList
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `resultIndex` | `number` | ✓ |  |
| `results` | `SpeechRecognitionResultList` | ✗ |  |

### `SpeechGrammar`

<details><summary>Interface Code</summary>

```ts
interface SpeechGrammar {
  src: string
  weight: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `src` | `string` | ✗ |  |
| `weight` | `number` | ✗ |  |

### `SpeechGrammarList`

<details><summary>Interface Code</summary>

```ts
interface SpeechGrammarList {
  readonly length: number
  addFromString: (string: string, weight?: number) => void
  addFromURI: (src: string, weight?: number) => void
  item: (index: number) => SpeechGrammar
  [index: number]: SpeechGrammar
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `length` | `number` | ✗ |  |
| `addFromString` | `(string: string, weight?: number) => void` | ✗ |  |
| `addFromURI` | `(src: string, weight?: number) => void` | ✗ |  |
| `item` | `(index: number) => SpeechGrammar` | ✗ |  |

### `SpeechRecognitionErrorEvent`

<details><summary>Interface Code</summary>

```ts
export interface SpeechRecognitionErrorEvent extends Event {
  readonly error: SpeechRecognitionErrorCode
  readonly message: string
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `error` | `SpeechRecognitionErrorCode` | ✗ |  |
| `message` | `string` | ✗ |  |

### `SpeechRecognitionEvent`

<details><summary>Interface Code</summary>

```ts
interface SpeechRecognitionEvent extends Event {
  readonly resultIndex: number
  readonly results: SpeechRecognitionResultList
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `resultIndex` | `number` | ✗ |  |
| `results` | `SpeechRecognitionResultList` | ✗ |  |

### `SpeechRecognitionEventMap`

<details><summary>Interface Code</summary>

```ts
interface SpeechRecognitionEventMap {
  audioend: Event
  audiostart: Event
  end: Event
  error: SpeechRecognitionErrorEvent
  nomatch: SpeechRecognitionEvent
  result: SpeechRecognitionEvent
  soundend: Event
  soundstart: Event
  speechend: Event
  speechstart: Event
  start: Event
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `audioend` | `Event` | ✗ |  |
| `audiostart` | `Event` | ✗ |  |
| `end` | `Event` | ✗ |  |
| `error` | `SpeechRecognitionErrorEvent` | ✗ |  |
| `nomatch` | `SpeechRecognitionEvent` | ✗ |  |
| `result` | `SpeechRecognitionEvent` | ✗ |  |
| `soundend` | `Event` | ✗ |  |
| `soundstart` | `Event` | ✗ |  |
| `speechend` | `Event` | ✗ |  |
| `speechstart` | `Event` | ✗ |  |
| `start` | `Event` | ✗ |  |

### `SpeechRecognition`

<details><summary>Interface Code</summary>

```ts
export interface SpeechRecognition extends EventTarget {
  continuous: boolean
  grammars: SpeechGrammarList
  interimResults: boolean
  lang: string
  maxAlternatives: number
  onaudioend: ((this: SpeechRecognition, ev: Event) => any) | null
  onaudiostart: ((this: SpeechRecognition, ev: Event) => any) | null
  onend: ((this: SpeechRecognition, ev: Event) => any) | null
  onerror: ((this: SpeechRecognition, ev: SpeechRecognitionErrorEvent) => any) | null
  onnomatch: ((this: SpeechRecognition, ev: SpeechRecognitionEvent) => any) | null
  onresult: ((this: SpeechRecognition, ev: SpeechRecognitionEvent) => any) | null
  onsoundend: ((this: SpeechRecognition, ev: Event) => any) | null
  onsoundstart: ((this: SpeechRecognition, ev: Event) => any) | null
  onspeechend: ((this: SpeechRecognition, ev: Event) => any) | null
  onspeechstart: ((this: SpeechRecognition, ev: Event) => any) | null
  onstart: ((this: SpeechRecognition, ev: Event) => any) | null
  abort: () => void
  start: () => void
  stop: () => void
  addEventListener: (<K extends keyof SpeechRecognitionEventMap>(type: K, listener: (this: SpeechRecognition, ev: SpeechRecognitionEventMap[K]) => any, options?: boolean | AddEventListenerOptions) => void) & ((type: string, listener: EventListenerOrEventListenerObject, options?: boolean | AddEventListenerOptions) => void)
  removeEventListener: (<K extends keyof SpeechRecognitionEventMap>(type: K, listener: (this: SpeechRecognition, ev: SpeechRecognitionEventMap[K]) => any, options?: boolean | EventListenerOptions) => void) & ((type: string, listener: EventListenerOrEventListenerObject, options?: boolean | EventListenerOptions) => void)
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `continuous` | `boolean` | ✗ |  |
| `grammars` | `SpeechGrammarList` | ✗ |  |
| `interimResults` | `boolean` | ✗ |  |
| `lang` | `string` | ✗ |  |
| `maxAlternatives` | `number` | ✗ |  |
| `onaudioend` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `onaudiostart` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `onend` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `onerror` | `((this: SpeechRecognition, ev: SpeechRecognitionErrorEvent) => any) | null` | ✗ |  |
| `onnomatch` | `((this: SpeechRecognition, ev: SpeechRecognitionEvent) => any) | null` | ✗ |  |
| `onresult` | `((this: SpeechRecognition, ev: SpeechRecognitionEvent) => any) | null` | ✗ |  |
| `onsoundend` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `onsoundstart` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `onspeechend` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `onspeechstart` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `onstart` | `((this: SpeechRecognition, ev: Event) => any) | null` | ✗ |  |
| `abort` | `() => void` | ✗ |  |
| `start` | `() => void` | ✗ |  |
| `stop` | `() => void` | ✗ |  |
| `addEventListener` | `(<K extends keyof SpeechRecognitionEventMap>(type: K, listener: (this: SpeechRecognition, ev: SpeechRecognitionEventMap[K]) => any, options?: boolean | AddEventListenerOptions) => void) & ((type: string, listener: EventListenerOrEventListenerObject, options?: boolean | AddEventListenerOptions) => void)` | ✗ |  |
| `removeEventListener` | `(<K extends keyof SpeechRecognitionEventMap>(type: K, listener: (this: SpeechRecognition, ev: SpeechRecognitionEventMap[K]) => any, options?: boolean | EventListenerOptions) => void) & ((type: string, listener: EventListenerOrEventListenerObject, options?: boolean | EventListenerOptions) => void)` | ✗ |  |


---

## Type Aliases

### `SpeechRecognitionErrorCode`

```ts
type SpeechRecognitionErrorCode = 'aborted' | 'audio-capture' | 'bad-grammar' | 'language-not-supported' | 'network' | 'no-speech' | 'not-allowed' | 'service-not-allowed';
```


---