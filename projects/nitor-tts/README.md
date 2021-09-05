Speech synthesis made easy - Browser based text to speech (TTS)
===

## Installation

```bash
npm install nitor-tts
```

## Description

Speech synthesis (tts) for the browser. Wrapping the browser Speech Synthesis API (https://developer.mozilla.org/en-US/docs/Web/API/SpeechSynthesis) and providing a similar interface, it improves it by :
-> init()  has optional paramters for volume,rate and pitch
-> speak() converts the text into speech with specified voice
- handling the fact that Chrome load voices in an asynchronous manner when others browsers don't
-> voice list supoort browser specific voice
- throwing specific exceptions: explicit exceptions will be thrown if you pass parameters with incompatible values to any of the methods

Work in Chrome, Edge and Mozila. 
See browser support here : http://caniuse.com/#feat=speech-synthesis

## Usage

Import the library :

```typescript
import NitorTTS from 'NitorTTS' // es6

```

Check for browser support :

```typescript
speech = new NitorTTS() // will throw an exception if not browser supported
if(speech.hasBrowserSupport()) { // returns a boolean
	console.log("speech synthesis supported")
}
```

Init the speech component :

```typescript
init(paremters)
```
You can pass the following properties to the init function:

- voice : the voice to use // default is chosen by your browser if not provided
- lang // default is determined by your browser if not provided
- volume // optional default is 1
- rate // optional default 1
- pitch //  optional default 1

```typescript
// Example with full conf 
init('Microsoft Zira - English (United States)','en-US',1,1);
```

Read a text :

```typescript
speech.speak{
	text: 'Hello, how are you today ?'}
```

You can pass the following properties to the speak function:
- text: text to be spoken

Pause talking in progress:

```typescript
Speech.pause()
```

Resume talking in progress:

```typescript
Speech.resume()
```

Cancel talking in progress:

```typescript
Speech.cancel()
```

Get boolean indicating if the utterance queue contains as-yet-unspoken utterances:

```typescript
Speech.pending()
```

Get boolean indicating if talking is paused:

```typescript
Speech.paused()
```

Get boolean indicating if talking is in progress:

```typescript
Speech.speaking()
```

