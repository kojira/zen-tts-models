# Blueskyちゃん（`bluesky`）

明るく高めの、若い女性の声です。「〜ですわ」「お見知りおきを」のような、上品なお嬢様口調によく合います。

- 声の高さ：ふつうに話して 260〜300 Hz 前後、うれしいときは 350 Hz 前後（下のサンプルで測った中央値）。
- 合成音声です。実在の人物の声ではありません。声は音声合成モデル VoxCPM2（Apache-2.0）で作り、ZEN-TTS 用に学習しました。
- 口調（お嬢様言葉）は、読ませる文章で決まります。モデルが勝手に言い回しを変えることはありません。

| 項目 | 内容 |
|---|---|
| id | `bluesky` |
| 版 | 1.1.0 |
| ファイル | [`bluesky.ztm`](https://github.com/kojira/zen-tts-models/releases/download/bluesky-v1.1.0/bluesky.ztm)（27,650,016 バイト、リリース [`bluesky-v1.1.0`](https://github.com/kojira/zen-tts-models/releases/tag/bluesky-v1.1.0)） |
| SHA-256 | `fccfa172ab5d687e617d62cbb7154d36ef2bc0394cba97ef4bb2abec7c92df93` |
| スタイル | `neutral`（ふつう）、`happy`（うれしい）、`sad`（かなしい）、`angry`（怒り）、`apologetic`（申し訳ない） |
| 対応 | [ZEN-TTS](https://github.com/zenryokukikai/zen-tts) 1.2.0 以降（G2P `33182b3f988e…`）。1.0.0（ZEN-TTS 1.1.0 用）はリリース [`bluesky-v1.0.0`](https://github.com/kojira/zen-tts-models/releases/tag/bluesky-v1.0.0) にあります |
| ライセンス | [LICENSE.md](../../LICENSE.md)（オープンソースのプロジェクトでのみ利用可、ソースコードに出典リンク） |

## サンプル

ZEN-TTS 1.2.0（公開版）で `bluesky.ztm`（1.1.0）から作りました（44.1 kHz、AAC 64 kbps、音量を -18 LUFS にそろえています）。

| スタイル | 文 | 音声 |
|---|---|---|
| neutral | 本日の会議は十時から始まります。 | [neutral.m4a](samples/neutral.m4a) |
| happy | 本当ですか、それはすごくうれしいです！ | [happy.m4a](samples/happy.m4a) |
| sad | 残念ですが、今回は見送ることになりました。 | [sad.m4a](samples/sad.m4a) |
| angry | 何度言ったらわかるのですか。 | [angry.m4a](samples/angry.m4a) |
| apologetic | お待たせしてしまい、申し訳ございません。 | [apologetic.m4a](samples/apologetic.m4a) |
| neutral（長め） | ごきげんよう、ブルースカイと申しますわ。本日はお越しいただき、まことにありがとうございます。わからないことがございましたら、どうぞ遠慮なくお尋ねくださいませ。 | [long-neutral.m4a](samples/long-neutral.m4a) |
| happy 70 ＋ neutral 30（長め） | わたくし、今日はとっても楽しみにしておりましたの！さあ、一緒にはじめましょう。 | [long-happy.m4a](samples/long-happy.m4a) |

## 使い方

[リポジトリの README](../../README.md#使い方) を見てください。

```js
const tts = await ZenTts.load({ modelsUrl: './models', cpuWasmUrl: './cpu/tts-cpu.wasm', model: './voices/bluesky.ztm' });
await tts.speak('ごきげんよう。ブルースカイと申しますわ。', { emotion: { happy: 60, neutral: 40 } });
```
