# suno-lyrics-skill

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [日本語](README.ja.md)

這是一個用來創作 Suno 歌詞和 Custom Mode 提示詞的 Codex skill。

它適合那種你不只是想要一個歌曲點子，而是想要一份可以直接貼進 Suno 試跑的內容。

它可以幫你寫歌詞、風格提示詞、排除風格、歌名、續寫段落、純音樂提示詞，也可以幫你修正那些跑偏的 Suno 生成結果。

## 它能做什麼

- 輸出完整的 Suno Custom Mode 四個欄位
- 寫出帶有清楚段落標籤的歌詞
- 生成 `Style of Music`，包含曲風、情緒、速度、樂器、人聲和製作質感
- 生成 `Exclude Styles`，把不想要的曲風、人聲或生成瑕疵排除掉
- 給出短、好搜、貼合 hook 的歌名
- 在既有歌詞後面續寫，而不是重新開一首歌
- 診斷 Suno 沒聽懂的地方，例如曲風、人聲、結構、副歌、樂器跑偏
- 處理純音樂需求，避免在正向提示裡寫入人聲描述

## 檔案說明

- `SKILL.md`，skill 入口、路由規則、輸出格式和品質檢查
- `SPEC.md`，實作說明和行為預期
- `SOURCES.md`，建立 skill 時使用的來源說明
- `references/structure-tags.md`，段落標籤、ad-lib、標點控制和續寫模式
- `references/lyric-craft.md`，hook、押韻、行長、原創性和改寫建議
- `references/style-prompts.md`，曲風配方、人聲描述、排除項和純音樂提示規則
- `references/troubleshooting.md`，修復糟糕 Suno 輸出的排查方法
- `references/examples.md`，輸出格式範例

## 怎麼使用

把這個資料夾安裝或放到 Codex skills 目錄裡，然後用正常語言提出 Suno 歌詞或提示詞需求。

skill 會判斷你真正需要的最小輸出。如果你要一整首歌，它會回傳 Custom Mode 的四個欄位。

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

如果你只需要歌詞、風格、排除項、歌名、續寫或故障排查，它只會回傳對應內容。

## 請求範例

完整 Custom Mode 提示：

```text
寫一首 Suno Custom Mode 歌，主題是搬到新城市以後假裝自己過得很好。中英雙語，深夜 synthpop，女聲。
```

只要歌詞：

```text
只給我歌詞，寫一首苦甜的 acoustic 歌，關於想念一個人，但並不想復合。
```

只要風格提示：

```text
只生成 Style of Music 欄位，做一首快節奏 cyberpunk rock，鼓要鋒利，副歌要很大。
```

純音樂：

```text
給我一個 Suno 純音樂提示詞，畫面是電影感沙漠追車，不要人聲。
```

續寫：

```text
從這個副歌繼續寫 bridge 和最終副歌。保持同樣情緒，不要重新開始整首歌。
```

故障排查：

```text
Suno 一直加 rap vocal，但我想要 clean indie pop。幫我診斷提示詞衝突並重寫欄位。
```

## 輸出範例

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

## 提示詞建議

給它一兩個具體細節就夠了。一個地點、一種情緒、一段關係、一個記憶，或者你腦子裡聽到的人聲質感。

好用的輸入大概長這樣：

- `分手後的雨夜公車`
- `普通話副歌，英文主歌`
- `柔和男聲，bedroom pop，不要太喪`
- `讓副歌更抓耳`
- `保留 verse 1，其他全部重寫`

不要要求模仿某位在世藝人的聲音。更好的方式是描述音樂特徵，例如速度、人聲質感、樂器、年代感、製作質感和情緒溫度。

## 注意事項

Suno 的提示詞結果有隨機性。這個 skill 的目標是減少跑偏，不是承諾精確控制每一個生成細節。

如果生成結果只是差一點，不要急著整份重寫。保留有效欄位，只修壞掉的欄位，通常更穩。
