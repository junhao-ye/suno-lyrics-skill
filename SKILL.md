---
name: suno-lyrics
description: Use when the user asks for Suno AI lyrics, Custom Mode song prompts, Lyrics/Style of Music/Exclude Styles/Title fields, ReMi-style lyric drafting, structure tags, rewrites, continuations, instrumental prompts, or troubleshooting bad AI music generations.
---

# Suno Lyrics

Use this skill to produce Suno-ready inputs for `Lyrics`, `Style of Music`, `Exclude Styles`, and `Title`. Favor Custom Mode when the user wants control over structure, language, mood, voice, arrangement, or revisions.

## First Move

Generate directly when the user gives a usable theme or intent. Ask one concise question only when the request has no song idea, no target output, or an unsafe request that must be redirected.

| Missing or unclear | Default behavior |
|--------------------|------------------|
| Language | Use the user's language; preserve requested bilingual split. |
| Style | Choose a genre/mood that fits the theme and state it in `Style of Music`. |
| Voice | Use neutral vocal traits unless the user asks for a voice type. |
| Length | Use a compact full-song structure; shorten if the user asks for a hook, chorus, jingle, or continuation. |
| Existing output | Treat as rewrite/troubleshooting and keep what already works. |

## Request Routes

| User wants... | Do | Open |
|---------------|----|------|
| Full Suno prompt or song | Return all four fields in order. | `references/structure-tags.md`, `references/lyric-craft.md`, `references/style-prompts.md` as needed |
| Lyrics only or rewrite | Return lyrics only unless Suno fields are requested. | `references/lyric-craft.md` |
| Style, excludes, or title only | Return only requested field labels. | `references/style-prompts.md` |
| Instrumental | Avoid vocal lyrics; give instrumental style, vocal excludes, title, and a note to enable Instrumental. | `references/style-prompts.md` |
| Continuation or Extend | Continue from the prior section, preserve language/style, and avoid restarting the whole song. | `references/structure-tags.md` |
| Bad Suno result | Diagnose the likely prompt conflict and provide a revised prompt. | `references/troubleshooting.md` |
| In-app lyric generation | Mention `Write with Suno`/ReMi only as an optional Suno-side workflow; still provide usable lyrics when asked. | `references/lyric-craft.md` |

## Runtime Workflow

1. Identify the route: new song, rewrite, style prompt, title, instrumental, continuation, or troubleshooting.
2. Decide the smallest useful output shape before writing.
3. Choose a compact structure and main hook before drafting lyrics.
4. Write singable, original lines with clear section tags and concrete imagery.
5. Build `Style of Music` with positive desired traits; move unwanted traits to `Exclude Styles`.
6. Return paste-ready fields without extra explanation unless a short note prevents likely Suno failure.

## Output Contract

For full Custom Mode requests, return:

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

For partial requests, keep the same field names but return only the requested fields. Do not wrap the final fields in extra commentary unless the user asks for explanation.

## Reference Routing

| Open when... | Read |
|--------------|------|
| choosing structure, section tags, ad-libs, continuation, or punctuation controls | `references/structure-tags.md` |
| writing or revising lyrics for hooks, rhyme, line length, originality, language, or ReMi-style drafting | `references/lyric-craft.md` |
| building `Style of Music`, `Exclude Styles`, instrumental prompts, vocal traits, or genre recipes | `references/style-prompts.md` |
| fixing bad Suno results such as wrong genre, unwanted vocals, weak chorus, ignored excludes, poor voice, or failed edits | `references/troubleshooting.md` |
| imitating output shape or adapting examples | `references/examples.md` |

## Suno-Specific Rules

| Rule | Do |
|------|----|
| Custom Mode | Supply explicit lyrics, style, excludes, and title when control matters. |
| Instrumental | Remove vocal terms from desired style, add vocal terms to excludes, and tell the user to enable Instrumental. |
| Reuse Prompt | For near-miss outputs, keep the best field and change only the broken field. |
| ReMi/Write with Suno | Use as optional in-product lyric drafting; do not rely on it when the user asked you to write the lyrics. |
| Style prompts | Prefer genre + mood + tempo + instruments + vocal + production texture. |
| Excludes | Use comma-separated unwanted genres, instruments, vocal traits, or production artifacts. |
| Voice control | Describe vocal traits; do not promise a specific singer unless the user has provided a Suno Voice/Persona workflow. |
| Copyright | Do not copy existing lyrics or imitate a living artist by name; translate references into musical traits. |

## Quality Gate

Before finalizing, check:

- Output shape matches the route and requested fields.
- Lyrics have a clear verse/chorus relationship when lyrics are included.
- Chorus or hook contains the main emotional or conceptual payoff.
- Line lengths are singable and not prose blocks.
- Style prompt does not contradict lyrics or excludes.
- Exclude Styles does not repeat desired traits or use vague negatives.
- Instrumental prompts contain no vocal-positive wording.
- Title is short, searchable, and aligned with the hook.

## Source Notes

Official Suno help checked on 2026-06-19 confirms Custom Mode accepts user lyrics and additional context, Advanced Options include Exclude, Reuse Prompt can revise lyrics/style/title for a new version, and ReMi is an optional lyric model in Custom Mode. Treat community tag tricks as useful but probabilistic.
