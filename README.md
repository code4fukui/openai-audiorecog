# openai-audiorecog

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

A Deno module for speech-to-text using OpenAI's Whisper API, configured for Japanese audio.

## Features

- Transcribes audio files using the OpenAI `whisper-1` model.
- Optimized for Japanese language transcription (`language: "ja"`).
- Provides both a command-line interface (CLI) and a JavaScript module.
- Automatically logs transcription requests and results to a local `log/` directory.

## Setup

1.  **Install Deno:** This tool requires the [Deno](https://deno.land/) runtime.

2.  **Get an OpenAI API Key:** Create a secret key from the [OpenAI API Keys](https://platform.openai.com/account/api-keys) page.

3.  **Configure Your Key:** Make the key available to the script in one of two ways:

    *   Create a `.env` file in the project root:
        ```
        OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxx
        ```
    *   Or, set an environment variable:
        ```sh
        export OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxx
        ```

## Usage

### As a CLI Tool

Transcribe an audio file directly from the command line and save the output to a text file.

```sh
deno run -A https://code4fukui.github.io/openai-audiorecog/cli.js audio.mp3 > audio.txt
```

### As a JavaScript Module

Import and use the `fetchAudioRecog` function in your Deno project.

```javascript
import { fetchAudioRecog } from "https://code4fukui.github.io/openai-audiorecog/fetchAudioRecog.js";

// Read an audio file into a Uint8Array
const mp3bin = new Uint8Array(await Deno.readFile("audio.mp3"));

// Get the transcribed text
const text = await fetchAudioRecog(mp3bin);

console.log(text);
```

## Demo

The repository includes an example script that transcribes the provided `audio.mp3`.

Run the demo:
```sh
deno run -A example.js
```

Expected output:
```
ようこそ、ようこそ、こんにちは。今日は日曜日です。
```

## API Details

This module interacts with the [OpenAI Audio Transcriptions API](https://platform.openai.com/docs/api-reference/audio) using the following parameters:
- **Model:** `whisper-1`
- **Language:** `ja` (Japanese)