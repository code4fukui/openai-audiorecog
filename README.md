# openai-audiorecog

Speech to text by OpenAI.

## Usage

```sh
deno run -A https://code4fukui.github.io/openai-audiorecog/cli.js audio.mp3 > audio.txt
```

```JavaScript
import { fetchAudioRecog } from "https://code4fukui.github.io/openai-audiorecog/fetchAudioRecog.js"

const fn = "audio.mp3";
const mp3bin = new Uint8Array(await Deno.readFile(fn));
const res = await fetchAudioRecog(mp3bin);
console.log(res);
```

## Setup

[create a secret key](https://beta.openai.com/docs/quickstart/build-your-application) on [OpenAI API](https://platform.openai.com/account/api-keys)

edit .env
```
OPENAI_API_KEY=****
```
or set the environment variables
```
export OPENAI_API_KEY=****
```

## Demo

```sh
deno run -A example.js
```
