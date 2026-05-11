# openai-audiorecog

OpenAIのWhisper APIを使用した、日本語音声に最適化された音声認識（Speech-to-Text）用のDenoモジュールです。

## 特徴

- OpenAIの `whisper-1` モデルを使用して音声ファイルを文字起こしします。
- 日本語の文字起こしに最適化されています（`language: "ja"`）。
- コマンドラインインターフェース（CLI）とJavaScriptモジュールの両方を提供します。
- 文字起こしのリクエストと結果をローカルの `log/` ディレクトリに自動的に記録します。

## セットアップ

1.  **Denoのインストール:** このツールには [Deno](https://deno.land/) ランタイムが必要です。

2.  **OpenAI APIキーの取得:** [OpenAI API Keys](https://platform.openai.com/account/api-keys) ページからシークレットキーを作成してください。

3.  **キーの設定:** 以下のいずれかの方法で、スクリプトからキーを利用できるようにします。

    *   プロジェクトルートに `.env` ファイルを作成する:
        ```
        OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxx
        ```
    *   または、環境変数を設定する:
        ```sh
        export OPENAI_API_KEY=sk-xxxxxxxxxxxxxxxxxxxxxxxx
        ```

## 使い方

### CLIツールとして

コマンドラインから直接音声ファイルを文字起こしし、結果をテキストファイルに保存します。

```sh
deno run -A https://code4fukui.github.io/openai-audiorecog/cli.js audio.mp3 > audio.txt
```

### JavaScriptモジュールとして

Denoプロジェクトで `fetchAudioRecog` 関数をインポートして使用します。

```javascript
import { fetchAudioRecog } from "https://code4fukui.github.io/openai-audiorecog/fetchAudioRecog.js";

// 音声ファイルをUint8Arrayとして読み込む
const mp3bin = new Uint8Array(await Deno.readFile("audio.mp3"));

// 文字起こしされたテキストを取得する
const text = await fetchAudioRecog(mp3bin);

console.log(text);
```

## デモ

リポジトリには、付属の `audio.mp3` を文字起こしするサンプルスクリプトが含まれています。

デモを実行:
```sh
deno run -A example.js
```

出力例:
```
ようこそ、ようこそ、こんにちは。今日は日曜日です。
```

## API詳細

このモジュールは、以下のパラメータを使用して [OpenAI Audio Transcriptions API](https://platform.openai.com/docs/api-reference/audio) にリクエストを送信します。
- **モデル:** `whisper-1`
- **言語:** `ja` （日本語）
