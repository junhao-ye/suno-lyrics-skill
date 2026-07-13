# suno-lyrics-skill

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [日本語](README.ja.md)

这是一个用于创作 Suno 歌词和 Custom Mode 提示词的 Codex skill。

它适合那种你不只是想要一个歌曲点子，而是想要一份可以直接粘贴到 Suno 里试跑的内容。

它可以帮你写歌词、风格提示词、排除风格、歌名、续写段落、纯音乐提示词，也可以帮你修正那些跑偏的 Suno 生成结果。

## 它能做什么

- 输出完整的 Suno Custom Mode 四个字段
- 写带有清晰段落标签的歌词
- 生成 `Style of Music`，包含曲风、情绪、速度、乐器、人声和制作质感
- 生成 `Exclude Styles`，把不想要的曲风、人声或生成瑕疵排除掉
- 给出短、好搜、贴合 hook 的歌名
- 在已有歌词后面续写，而不是重新开一首歌
- 诊断 Suno 没听懂的地方，比如曲风、人声、结构、副歌、乐器跑偏
- 处理纯音乐需求，避免在正向提示里写入人声描述

## 文件说明

- `SKILL.md`，skill 入口、路由规则、输出格式和质量检查
- `SPEC.md`，实现说明和行为预期
- `SOURCES.md`，构建 skill 时使用的来源说明
- `references/structure-tags.md`，段落标签、ad-lib、标点控制和续写模式
- `references/lyric-craft.md`，hook、押韵、行长、原创性和改写建议
- `references/style-prompts.md`，曲风配方、人声描述、排除项和纯音乐提示规则
- `references/troubleshooting.md`，修复糟糕 Suno 输出的排查方法
- `references/examples.md`，输出格式示例

## 怎么使用

把这个文件夹安装或放到 Codex skills 目录里，然后用正常语言提出 Suno 歌词或提示词需求。

skill 会判断你真正需要的最小输出。如果你要一整首歌，它会返回 Custom Mode 的四个字段。

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

如果你只需要歌词、风格、排除项、歌名、续写或故障排查，它只会返回对应内容。

## 请求示例

完整 Custom Mode 提示：

```text
写一首 Suno Custom Mode 歌，主题是搬到新城市以后假装自己过得很好。中英双语，深夜 synthpop，女声。
```

只要歌词：

```text
只给我歌词，写一首苦甜的 acoustic 歌，关于想念一个人，但并不想复合。
```

只要风格提示：

```text
只生成 Style of Music 字段，做一首快节奏 cyberpunk rock，鼓要锋利，副歌要很大。
```

纯音乐：

```text
给我一个 Suno 纯音乐提示词，画面是电影感沙漠追车，不要人声。
```

续写：

```text
从这个副歌继续写 bridge 和最终副歌。保持同样情绪，不要重新开始整首歌。
```

故障排查：

```text
Suno 一直加 rap vocal，但我想要 clean indie pop。帮我诊断提示词冲突并重写字段。
```

## 输出示例

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

## 提示词建议

给它一两个具体细节就够了。一个地点、一种情绪、一段关系、一个记忆，或者你脑子里听到的人声质感。

好用的输入大概长这样：

- `分手后的雨夜公交`
- `普通话副歌，英文主歌`
- `柔和男声，bedroom pop，不要太丧`
- `让副歌更抓耳`
- `保留 verse 1，其他全部重写`

不要要求模仿某位在世艺人的声音。更好的方式是描述音乐特征，比如速度、人声质感、乐器、年代感、制作质感和情绪温度。

## 注意事项

Suno 的提示词结果有随机性。这个 skill 的目标是减少跑偏，不是承诺精确控制每一个生成细节。

如果生成结果只是差一点，不要急着整份重写。保留有效字段，只修坏掉的字段，通常更稳。

## License

MIT License。详见 [LICENSE](LICENSE)。
