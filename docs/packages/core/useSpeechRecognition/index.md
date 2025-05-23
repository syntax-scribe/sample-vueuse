[⬅️ Back to Table of Contents](../../../index.md)

# 📄 `index.ts`

## 📚 Table of Contents

- [Imports](#imports)
- [Functions](#functions)
- [Interfaces](#interfaces)
- [Type Aliases](#type-aliases)

## 📊 Analysis Summary

- **Functions**: 4
- **Classes**: 0
- **Imports**: 11
- **Interfaces**: 1
- **Type Aliases**: 1

## 🛠️ File Location:
📂 **`packages/core/useSpeechRecognition/index.ts`**

## 📦 Imports

| Name | Source |
|------|--------|
| `MaybeRefOrGetter` | `vue` |
| `ConfigurableWindow` | `../_configurable` |
| `SpeechRecognition` | `./types` |
| `SpeechRecognitionErrorEvent` | `./types` |
| `toRef` | `@vueuse/shared` |
| `tryOnScopeDispose` | `@vueuse/shared` |
| `shallowRef` | `vue` |
| `toValue` | `vue` |
| `watch` | `vue` |
| `defaultWindow` | `../_configurable` |
| `useSupported` | `../useSupported` |


---

## Functions

### `useSpeechRecognition(options: UseSpeechRecognitionOptions): { isSupported: any; isListening: any; isFinal: any; recognition: SpeechRecognition; result: any; error: any; toggle: (value?: boolean) => void; start: () => void; stop: () => void; }`

<details><summary>Code</summary>

```ts
export function useSpeechRecognition(options: UseSpeechRecognitionOptions = {}) {
  const {
    interimResults = true,
    continuous = true,
    maxAlternatives = 1,
    window = defaultWindow,
  } = options

  const lang = toRef(options.lang || 'en-US')
  const isListening = shallowRef(false)
  const isFinal = shallowRef(false)
  const result = shallowRef('')
  const error = shallowRef<SpeechRecognitionErrorEvent | undefined>(undefined)

  let recognition: SpeechRecognition | undefined

  const start = () => {
    isListening.value = true
  }

  const stop = () => {
    isListening.value = false
  }

  const toggle = (value = !isListening.value) => {
    if (value) {
      start()
    }
    else {
      stop()
    }
  }

  const SpeechRecognition = window && ((window as any).SpeechRecognition || (window as any).webkitSpeechRecognition)
  const isSupported = useSupported(() => SpeechRecognition)

  if (isSupported.value) {
    recognition = new SpeechRecognition() as SpeechRecognition

    recognition.continuous = continuous
    recognition.interimResults = interimResults
    recognition.lang = toValue(lang)
    recognition.maxAlternatives = maxAlternatives

    recognition.onstart = () => {
      isListening.value = true
      isFinal.value = false
    }

    watch(lang, (lang) => {
      if (recognition && !isListening.value)
        recognition.lang = lang
    })

    recognition.onresult = (event) => {
      const currentResult = event.results[event.resultIndex]
      const { transcript } = currentResult[0]

      isFinal.value = currentResult.isFinal
      result.value = transcript
      error.value = undefined
    }

    recognition.onerror = (event) => {
      error.value = event
    }

    recognition.onend = () => {
      isListening.value = false
      recognition!.lang = toValue(lang)
    }

    watch(isListening, (newValue, oldValue) => {
      if (newValue === oldValue)
        return

      if (newValue)
        recognition!.start()
      else
        recognition!.stop()
    })
  }

  tryOnScopeDispose(() => {
    stop()
  })

  return {
    isSupported,
    isListening,
    isFinal,
    recognition,
    result,
    error,

    toggle,
    start,
    stop,
  }
}
```
</details>

- **JSDoc**:
```ts
/**
 * Reactive SpeechRecognition.
 *
 * @see https://vueuse.org/useSpeechRecognition
 * @see https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition SpeechRecognition
 * @param options
 */
```

- **Parameters**:
  - `options: UseSpeechRecognitionOptions`
- **Return Type**: `{ isSupported: any; isListening: any; isFinal: any; recognition: SpeechRecognition; result: any; error: any; toggle: (value?: boolean) => void; start: () => void; stop: () => void; }`
- **Calls**:
  - `toRef (from @vueuse/shared)`
  - `shallowRef (from vue)`
  - `start`
  - `stop`
  - `useSupported (from ../useSupported)`
  - `toValue (from vue)`
  - `watch (from vue)`
  - `recognition!.start`
  - `recognition!.stop`
  - `tryOnScopeDispose (from @vueuse/shared)`
### `start(): void`

<details><summary>Code</summary>

```ts
() => {
    isListening.value = true
  }
```
</details>

- **Return Type**: `void`
### `stop(): void`

<details><summary>Code</summary>

```ts
() => {
    isListening.value = false
  }
```
</details>

- **Return Type**: `void`
### `toggle(value: boolean): void`

<details><summary>Code</summary>

```ts
(value = !isListening.value) => {
    if (value) {
      start()
    }
    else {
      stop()
    }
  }
```
</details>

- **Parameters**:
  - `value: boolean`
- **Return Type**: `void`
- **Calls**:
  - `start`
  - `stop`

---

## Classes

> No classes found in this file.


---

## Interfaces

### `UseSpeechRecognitionOptions`

<details><summary>Interface Code</summary>

```ts
export interface UseSpeechRecognitionOptions extends ConfigurableWindow {
  /**
   * Controls whether continuous results are returned for each recognition, or only a single result.
   *
   * @default true
   */
  continuous?: boolean
  /**
   * Controls whether interim results should be returned (true) or not (false.) Interim results are results that are not yet final
   *
   * @default true
   */
  interimResults?: boolean
  /**
   * Language for SpeechRecognition
   *
   * @default 'en-US'
   */
  lang?: MaybeRefOrGetter<string>
  /**
   * A number representing the maximum returned alternatives for each result.
   *
   * @see https://developer.mozilla.org/en-US/docs/Web/API/SpeechRecognition/maxAlternatives
   * @default 1
   */
  maxAlternatives?: number
}
```
</details>

#### Properties

| Name | Type | Optional | Description |
|------|------|----------|-------------|
| `continuous` | `boolean` | ✓ |  |
| `interimResults` | `boolean` | ✓ |  |
| `lang` | `MaybeRefOrGetter<string>` | ✓ |  |
| `maxAlternatives` | `number` | ✓ |  |


---

## Type Aliases

### `UseSpeechRecognitionReturn`

```ts
type UseSpeechRecognitionReturn = ReturnType<typeof useSpeechRecognition>;
```


---