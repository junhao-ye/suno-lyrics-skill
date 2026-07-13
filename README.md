# suno-lyrics-skill

[English](README.md) | [简体中文](README.zh-CN.md) | [繁體中文](README.zh-TW.md) | [日本語](README.ja.md)

Codex skill package for writing Suno-ready lyrics and Custom Mode prompts.

This skill is for the moment when you do not just want a song idea.

You want something you can paste into Suno and actually try.

It helps draft lyrics, style prompts, exclude styles, titles, continuations, instrumental prompts, and fixes for messy generations.

## What It Does

- Writes full Suno Custom Mode fields
- Drafts lyrics with clear section tags
- Creates `Style of Music` prompts with genre, mood, tempo, instruments, vocals, and production texture
- Builds `Exclude Styles` so unwanted genres, vocals, or artifacts are kept out of the prompt
- Suggests short, searchable song titles
- Continues an existing song without restarting the whole structure
- Troubleshoots outputs that missed the genre, chorus, voice, structure, or instrumentation
- Handles instrumental prompts by avoiding vocal-positive wording

## Files

- `SKILL.md` - the skill entrypoint, routing rules, output contract, and quality gate
- `SPEC.md` - implementation notes and expected behavior
- `SOURCES.md` - source notes used while building the skill
- `references/structure-tags.md` - section tags, ad-libs, punctuation, and continuation patterns
- `references/lyric-craft.md` - hook writing, rhyme, line length, originality, and rewrite guidance
- `references/style-prompts.md` - genre recipes, vocal traits, excludes, and instrumental prompt rules
- `references/troubleshooting.md` - fixes for bad Suno outputs
- `references/examples.md` - sample output shapes

## How To Use

Install or place this folder as a Codex skill, then ask for Suno lyrics or prompt fields in normal language.

The skill will choose the smallest useful output shape. If you ask for a full song, it returns all four Custom Mode fields.

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

If you only ask for lyrics, style, excludes, title, continuation, or troubleshooting, it returns only what you need.

## Example Requests

Full Custom Mode prompt:

```text
Write a Suno Custom Mode song about moving to a new city and pretending I am fine. Make it bilingual English and Mandarin, late-night synthpop, female vocal.
```

Lyrics only:

```text
Give me lyrics only for a bittersweet acoustic song about missing someone but not wanting them back.
```

Style prompt only:

```text
Create only the Style of Music field for a fast cyberpunk rock track with sharp drums and a huge chorus.
```

Instrumental:

```text
Make an instrumental Suno prompt for a cinematic desert chase scene, no vocals.
```

Continuation:

```text
Continue from this chorus and write the bridge plus final chorus. Keep the same emotional tone and do not restart the song.
```

Troubleshooting:

```text
Suno keeps adding rap vocals, but I wanted clean indie pop. Diagnose the prompt and rewrite the fields.
```

## Output Example

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

## Prompting Tips

Give the skill one or two concrete details. A place, a mood, a relationship, a memory, or the kind of voice you hear in your head.

Good inputs look like this:

- `rainy bus ride after a breakup`
- `Mandarin chorus, English verses`
- `soft male vocal, bedroom pop, not too sad`
- `make the chorus more memorable`
- `keep verse 1, rewrite everything else`

Avoid asking for the sound of a specific living artist. Describe the musical traits instead, such as tempo, vocal tone, instruments, era, production texture, and emotional temperature.

## Notes

Suno prompt behavior is probabilistic. The skill is designed to reduce confusion, not promise exact control.

For near-miss outputs, reuse what worked and revise only the broken field. Usually that beats rewriting the whole prompt from scratch.

## License

MIT License. See [LICENSE](LICENSE).
