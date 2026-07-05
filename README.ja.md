# suno-lyrics-skill

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [日本語](README.ja.md)

Suno 用の歌詞と Custom Mode プロンプトを書くための Codex skill です。

ただ曲のアイデアがほしいだけではなく、Suno にそのまま貼り付けて試せる形がほしいときに使います。

歌詞、スタイルプロンプト、除外スタイル、タイトル、続きの歌詞、インストゥルメンタル用プロンプト、うまくいかなかった生成結果の修正まで扱えます。

## できること

- Suno Custom Mode の4つのフィールドをまとめて作成
- セクションタグ付きの歌詞を作成
- ジャンル、ムード、テンポ、楽器、ボーカル、プロダクション感を含む `Style of Music` を作成
- 不要なジャンル、ボーカル、生成ノイズを避けるための `Exclude Styles` を作成
- 短く検索しやすく、hook に合うタイトルを提案
- 既存の歌詞を最初から作り直さずに続きだけを書く
- ジャンル、ボーカル、構成、サビ、楽器がずれた Suno 出力を診断
- インストゥルメンタルでは、正方向のプロンプトにボーカル表現を入れないように調整

## ファイル構成

- `SKILL.md` - skill の入口、ルーティング規則、出力形式、品質チェック
- `SPEC.md` - 実装メモと期待される挙動
- `SOURCES.md` - skill 作成時の参照元メモ
- `references/structure-tags.md` - セクションタグ、ad-lib、句読点の使い方、続きを書くパターン
- `references/lyric-craft.md` - hook、韻、行の長さ、オリジナリティ、リライトのガイド
- `references/style-prompts.md` - ジャンルレシピ、ボーカル表現、除外項目、インストゥルメンタルのルール
- `references/troubleshooting.md` - うまくいかない Suno 出力の修正方法
- `references/examples.md` - 出力例

## 使い方

このフォルダを Codex skills のディレクトリに配置またはインストールしてから、Suno の歌詞やプロンプトの要望を自然な言葉で伝えます。

skill は必要な最小限の出力形式を判断します。フルソングを依頼した場合は、Custom Mode の4つのフィールドを返します。

```markdown
1. Lyrics

[Intro: ...]
...

2. Style of Music
...

3. Exclude Styles
...

4. Title
...
```

歌詞だけ、スタイルだけ、除外項目だけ、タイトルだけ、続きを書く、トラブルシューティングだけ、といった依頼なら、必要な部分だけを返します。

## 依頼例

Custom Mode 用の完全なプロンプト：

```text
新しい街に引っ越して、平気なふりをしている人の Suno Custom Mode 曲を書いて。英語と中国語のバイリンガル、深夜の synthpop、女性ボーカル。
```

歌詞だけ：

```text
歌詞だけください。誰かをまだ恋しく思っているけれど、よりを戻したいわけではない、ほろ苦い acoustic 曲にして。
```

スタイルだけ：

```text
Style of Music フィールドだけ作って。速い cyberpunk rock、鋭いドラム、大きなサビ。
```

インストゥルメンタル：

```text
映画的な砂漠のカーチェイスをイメージした Suno のインストゥルメンタル用プロンプトを作って。ボーカルなし。
```

続きを書く：

```text
このサビの続きとして bridge と最後のサビを書いて。同じ感情のまま、曲全体を最初から書き直さないで。
```

トラブルシューティング：

```text
Suno が毎回 rap vocal を入れてくるけど、ほしいのは clean indie pop。プロンプトの衝突を診断して、フィールドを書き直して。
```

## 出力例

```markdown
1. Lyrics

[Intro: soft synth pulse, distant city noise]
Streetlights blink like they know my name
I tell the mirror I am doing okay

[Verse 1]
New keys, new room, same old phone
Half my life still packed in boxes
I laugh too loud when I feel alone
Nobody asks what the silence costs

[Chorus]
I am fine, I am fine
Said it so much it almost rhymes
Ni shuo bie pa, wo shuo wo zai
But the night still finds me every time

2. Style of Music
late-night synthpop, 92 BPM, warm female vocal, pulsing analog synth bass, soft gated drums, glassy pads, intimate verses, wide emotional chorus, clean modern production

3. Exclude Styles
rap vocals, metal guitars, EDM drop, lo-fi distortion, male vocal, spoken word, harsh autotune

4. Title
Almost Fine
```

## プロンプトのコツ

具体的なディテールを1つか2つ入れるだけで十分です。場所、気分、関係性、記憶、頭の中で鳴っている声の質感などです。

使いやすい入力例：

- `別れた後の雨の夜のバス`
- `中国語のサビ、英語の verse`
- `柔らかい男性ボーカル、bedroom pop、暗すぎない`
- `サビをもっと耳に残るように`
- `verse 1 は残して、それ以外を全部書き直して`

存命アーティストの声を直接まねる依頼は避けてください。代わりに、テンポ、声質、楽器、時代感、プロダクションの質感、感情の温度を説明するほうが安定します。

## 注意

Suno のプロンプト結果にはランダム性があります。この skill はずれを減らすためのもので、すべての生成結果を完全に制御するものではありません。

生成結果が惜しい場合は、全部を書き直すより、うまくいったフィールドを残して、壊れているフィールドだけを直すほうが安定します。
