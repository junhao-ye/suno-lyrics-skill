# Suno Lyrics Sources

## Source Inventory

| Source | Use | Notes |
|--------|-----|-------|
| Suno Help: Can I use my own lyrics? | Confirms Custom Mode can accept user lyrics and provide more detail. | Official source checked 2026-06-19. |
| Suno Help: Android Create Custom Mode | Confirms custom flow includes lyrics, instrumental toggle, styles/advanced options, and title. | Official source checked 2026-05-25. |
| Suno Help: Can I change the voice or lyrics in my song? | Confirms Reuse Prompt can edit Lyrics, Style of Music, and Title for a new version. | Official source checked 2026-06-19. |
| Suno Help: My Taste | Confirms Styles area and style augmentation context. | Official source checked 2026-05-25. |
| Suno Help: How do I exclude elements of a song? | Confirms Exclude lives in Advanced Options for Custom Mode and accepts unwanted instruments or other details. | Official source checked 2026-06-19. |
| Suno Help: What is ReMi? | Confirms ReMi is an optional lyric model available through `Write with Suno` in Custom Mode. | Official source checked 2026-06-19. |
| Existing `suno-lyrics/SKILL.md` | Provided prior tag library, style examples, punctuation notes, cliche watchlist, and output shape. | Converted from monolithic guide to routed references. |

## Decisions

- Chose `reference-backed-expert` shape because most invocations only need the four-field runtime contract, while tag libraries, examples, and troubleshooting are branch-specific.
- Added `SPEC.md` because scope, trigger strategy, evidence policy, and reference architecture materially changed.
- Kept community tag tricks as probabilistic guidance; official Suno help does not guarantee every bracket tag or exclude will be obeyed.
- Split runtime behavior by request route so partial requests do not receive unnecessary lyric blocks.
- Added instrumental and Reuse Prompt handling because official Suno docs separate new-generation prompting from editing rendered audio.

## Description Test Set

Should trigger:
- "幫我寫一首 Suno 歌，中文女聲，失戀"
- "給我 Suno custom mode 的 lyrics、style、exclude、title"
- "Suno 老是生成男聲，幫我改 prompt"
- "把這首歌改成 EDM drop 結構"
- "我要 Suno 風格提示詞，不要歌詞"
- "做一個 Suno 純音樂 prompt，不要人聲"
- "Suno 生成出來聲音不對，幫我用 Reuse Prompt 改"
- "給我 ReMi 可以用的歌詞題目和成品歌詞"

Should not trigger:
- "分析這首歌的和弦走向"
- "幫我混音人聲"
- "寫一首普通現代詩"
- "查詢 Suno 會員價格"
- "生成 Midjourney 音樂封面 prompt"

## Open Gaps

- No persistent user-approved holdout examples yet.
- No automated validator specific to Suno output quality or Suno model compliance.
- Suno UI and model behavior may change; re-check official help for product-specific fields when precision matters.
