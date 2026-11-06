# zen-tts-models

日本語の音声合成 [ZEN-TTS](https://github.com/zenryokukikai/zen-tts)（[全力機械](https://zenryokukikai.com)）で使える voice のモデル（`.ztm`）を配布するリポジトリです。voice は順次追加します。

- モデルはオープンソースのプロジェクトでのみ使えます。ソースコードに出典リンクを書いてください（[ライセンス](#ライセンス)）。
- ここの voice は、すべて合成音声です。実在の人物の声ではありません。

## voice の一覧

| id | 名前 | 声 | スタイル | 版 | ダウンロード | 大きさ | SHA-256 | サンプル |
|---|---|---|---|---|---|---|---|---|
| `bluesky` | [Blueskyちゃん](voices/bluesky/) | 明るく高めの、若い女性の声。上品なお嬢様口調によく合う | neutral / happy / sad / angry / apologetic | 1.1.1 | [bluesky.ztm](https://github.com/kojira/zen-tts-models/releases/download/bluesky-v1.1.1/bluesky.ztm) | 27.7 MB | `e8cac44a…82bd98cc`（[全体](voices/bluesky/voice.json)） | [neutral](voices/bluesky/samples/neutral.m4a)・[happy](voices/bluesky/samples/happy.m4a)・[sad](voices/bluesky/samples/sad.m4a)・[angry](voices/bluesky/samples/angry.m4a)・[apologetic](voices/bluesky/samples/apologetic.m4a)・[長め](voices/bluesky/samples/long-neutral.m4a) |

- 機械で読める一覧：[`voices.json`](voices.json)。voice ごとの詳細：`voices/<id>/voice.json`。
- 配布は voice ごとの GitHub リリース（タグ `<id>-v<版>`、添付ファイル `<id>.ztm`）です。モデルはリポジトリには入れていません。

## 使い方

ZEN-TTS 1.3.0 以降で、`model` に `.ztm` を指定します（Blueskyちゃん 1.1.0 は ZEN-TTS 1.2.x 用で、リリース [`bluesky-v1.1.0`](https://github.com/kojira/zen-tts-models/releases/tag/bluesky-v1.1.0) に、1.0.0 は ZEN-TTS 1.1.0 用で、リリース [`bluesky-v1.0.0`](https://github.com/kojira/zen-tts-models/releases/tag/bluesky-v1.0.0) に残しています）。読み（G2P）は ZEN-TTS の `models/g2p/` を使います（ZEN-TTS のリポジトリ・パッケージに入っています）。

1. `.ztm` をダウンロードします（`sha256sum bluesky.ztm` で、上の SHA-256 と同じか確かめてください）。
2. **ブラウザ**：`.ztm` を自分のサイトに置いて、その URL を指定します。

   ```js
   import { ZenTts } from './dist/index.js';   // ZEN-TTS
   const tts = await ZenTts.load({ modelsUrl: './models', cpuWasmUrl: './cpu/tts-cpu.wasm', model: './voices/bluesky.ztm' });
   const r = await tts.speak('ごきげんよう。ブルースカイと申しますわ。', { emotion: { happy: 60, neutral: 40 } });
   ```

   GitHub のリリースの URL は、ブラウザから直接は読めません（ダウンロード先が CORS のヘッダーを返さないため）。ダウンロードして、自分のサイトか CDN に置いてください。
3. **Node.js**：ローカルのパスを指定します。

   ```js
   import { ZenTtsNode, wavBytes } from 'zen-tts/node';
   import { writeFileSync } from 'node:fs';
   const tts = await ZenTtsNode.load({ model: './bluesky.ztm' });
   const r = await tts.speak('本日はご来店いただき、ありがとうございます。', { emotion: { neutral: 100 } });
   writeFileSync('voice.wav', wavBytes(r.pcm));
   ```

感情の指定、文中の変化、辞書などは [ZEN-TTS の README](https://github.com/zenryokukikai/zen-tts#readme) を見てください。

## クレジットと出典（必須）

使うときは、次の 2 つを両方守ってください。

1. **ZEN-TTS のクレジット**（[ZEN-TTS ライセンス 1.0](https://github.com/zenryokukikai/zen-tts/blob/main/LICENSE.md)）：アプリ・サイト・作品の利用者が見つけられる場所に、「音声合成：ZEN-TTS（https://zenryokukikai.com ）」を表示します。
2. **このリポジトリのモデルの出典**（[LICENSE.md](LICENSE.md)）：使うプロジェクトのソースコードの中（README、ソースのコメント、NOTICE など）に、voice の名前・このリポジトリの URL・全力機械の URL を書きます。

   ```
   音声モデル：Blueskyちゃん（https://github.com/kojira/zen-tts-models ）／ ZEN-TTS（https://zenryokukikai.com ）
   ```

## ライセンス

- 音声モデル・サンプル・文書：[LICENSE.md](LICENSE.md)（zen-tts-models 音声モデル ライセンス 1.0）
  - オープンソースのプロジェクト（ソースコードを公開し、OSI が承認したライセンスで配布しているもの）でのみ使えます。そのソースコードやリポジトリに、モデルのファイルを含めても構いません。
  - オープンソースでないプロジェクトでは使えません。
  - 使うプロジェクトのソースコードに、出典リンクを書いてください。
- 再生に使う ZEN-TTS：[ZEN-TTS ライセンス 1.0](https://github.com/zenryokukikai/zen-tts/blob/main/LICENSE.md)（全力機械株式会社）

## リンク

- ZEN-TTS：https://github.com/zenryokukikai/zen-tts
- 全力機械：https://zenryokukikai.com

---

## English

Voice models (`.ztm`) for the Japanese text-to-speech engine [ZEN-TTS](https://github.com/zenryokukikai/zen-tts) by [Zenryoku Kikai](https://zenryokukikai.com). More voices will be added over time. All voices here are synthetic, not real people's voices.

| id | Name | Styles | Version | Download | SHA-256 |
|---|---|---|---|---|---|
| `bluesky` | Bluesky-chan (Blueskyちゃん) — a bright, high-pitched young woman's voice that suits an elegant "ojousama" way of speaking | neutral / happy / sad / angry / apologetic | 1.1.1 | [bluesky.ztm](https://github.com/kojira/zen-tts-models/releases/download/bluesky-v1.1.1/bluesky.ztm) (27.7 MB) | `e8cac44a6c24a23a0eebd819e9214ad4d9c0af817ea172de2b5e67f082bd98cc` |

- Use with ZEN-TTS 1.3.0 or later (Bluesky-chan 1.1.0, for ZEN-TTS 1.2.x, stays in the release `bluesky-v1.1.0`; 1.0.0, for ZEN-TTS 1.1.0, in `bluesky-v1.0.0`): `ZenTts.load({ modelsUrl, model: '<url of the .ztm>' })` or `ZenTtsNode.load({ model: './bluesky.ztm' })`. Download the file and host it yourself: GitHub release URLs can't be fetched directly from a browser (no CORS headers).
- **License** ([LICENSE.md](LICENSE.md)): the models may be used **only in open-source projects** (source code public, under an OSI-approved license); including the model file in such a project's source or repository is allowed. Use in projects that are not open source is not allowed. Put an attribution in the project's source code: the voice name, https://github.com/kojira/zen-tts-models and https://zenryokukikai.com.
- ZEN-TTS itself is under the [ZEN-TTS License 1.0](https://github.com/zenryokukikai/zen-tts/blob/main/LICENSE.md), which requires the credit "Speech synthesis: ZEN-TTS (https://zenryokukikai.com )".
- Machine-readable index: [`voices.json`](voices.json).
