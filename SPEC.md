# Suno Lyrics Specification

## Intent

`suno-lyrics` helps agents create paste-ready Suno custom mode inputs with strong lyrics, controlled song structure, style prompts, excludes, and titles. It should behave like a practical music prompt and lyric writing assistant, not a loose encyclopedia of tags.

## Scope

In scope:
- New Suno lyric generation.
- Suno custom mode prompt fields.
- Song structure tags, ad-libs, style prompts, excludes, and titles.
- Prompt troubleshooting after a poor generation.
- Original lyric rewrites and continuation support.
- Instrumental prompts and vocal-exclusion guidance.
- In-app lyric workflow guidance for `Write with Suno`/ReMi when relevant.

Out of scope:
- Copying existing copyrighted lyrics.
- Producing a living artist imitation by name.
- Guaranteeing Suno will obey every tag or exclude.
- Audio editing, stem extraction, publishing, licensing, or account operations.

## Users And Trigger Context

- Primary users: creators making AI-generated songs in Suno.
- Common user requests: "寫一首 Suno 歌", "幫我做 Suno prompt", "lyrics/style/exclude/title", "改成副歌更洗腦", "Suno 老是跑出人聲", "我要純音樂", "幫我改 Reuse Prompt".
- Should not trigger for: general poetry unrelated to songs, non-Suno music theory, or manual audio production.

## Runtime Contract

- Required first actions: identify the route, then use defaults unless one concise question is necessary.
- Required outputs: full Custom Mode requests use `Lyrics`, `Style of Music`, `Exclude Styles`, and `Title`; partial requests return only requested Suno field labels.
- Non-negotiable constraints: keep lyrics original, singable, structured, and Suno-paste-ready.
- Expected bundled files loaded at runtime: only the references needed for the requested branch.

## Source And Evidence Model

Authoritative sources:
- Official Suno help articles about Custom mode, custom lyrics, instrumental mode, Reuse Prompt, and Style fields.
- Official Suno help articles about Exclude and ReMi/Write with Suno.

Useful improvement sources:
- accepted user outputs.
- failed Suno generations and the prompt that caused them.
- community heuristics that survive repeated use, stored as probabilistic guidance.

Data that must not be stored:
- unpublished client lyrics unless explicitly intended as examples.
- private release plans, names, or campaign details.
- copied lyrics from existing songs.

## Reference Architecture

- `SKILL.md` contains trigger description, workflow, output contract, routing, and quality gate.
- `references/structure-tags.md` contains section tags and performance notation.
- `references/lyric-craft.md` contains lyric writing and revision guidance.
- `references/style-prompts.md` contains Style of Music and Exclude Styles guidance.
- `references/troubleshooting.md` contains Suno failure diagnosis.
- `references/examples.md` contains compact transformed examples.
- `scripts/` and `assets/` are not currently used.

## Validation

- Lightweight validation: check frontmatter, reference paths, and output contract.
- Deeper validation: test the skill against a new song request, a rewrite request, a style-only request, an instrumental request, a continuation request, and a troubleshooting request.
- Acceptance gates: paste-ready four-field output, clear routing references, no host-specific paths, no hidden required instructions inside optional references.

## Known Limitations

- Suno behavior changes over time and can ignore some tags or excludes.
- The skill can improve prompt quality but cannot guarantee a specific melody, vocalist, pronunciation, or mix.
- Latest product UI details should be verified against official Suno help when precision matters.

## Maintenance Notes

- Update `SKILL.md` when triggers, output contract, routing, or safety rules change.
- Update references when a branch grows, shrinks, or proves unreliable.
- Update `SOURCES.md` when official Suno guidance or community evidence changes the skill's assumptions.
